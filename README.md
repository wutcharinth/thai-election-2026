# Thai Election 2569 Raw Data Analysis Project

This project contains the **actual official structured dataset** for the 2569 (2026) Thai General Election, parsed and converted into a SQLite Database. Since the original Google Drive links containing the PDF announcements (สส. 6/1) are difficult to access/scrape directly, we are using an open-source civic effort dataset that has already fully parsed the 776 raw PDFs using multi-modal AI and verified the results.

## Data Source
The raw data comes from the official Election Commission of Thailand (ECT). The parsed, QA'd dataset is cloned from an open-source civic tech repository: `killernay/election-69-OCR-result`.

## What I've Built For You

1. **`election-69-OCR-result/`**: This directory contains the complete cloned repository of the 2026 election data, including detailed JSONs and CSVs for constituency and party lists.
2. **`build_database.py`**: A clean Python script that takes the parsed CSV tables from the cloned repository and inserts them into a structured database.
3. **`election_2569.db`**: The SQLite data file containing the finalized, structured real 2569 election data!

### Database Structure (`election_2569.db`)
The SQLite database contains 3 main tables:

*   **`constituency_results`**: Contains results for all candidates across every district (3,372 rows). 
    *   *Columns*: province_code, province, area_no, candidate_no, name, party, vote_score.
*   **`party_list_results`**: Contains the party list vote counts for every district (22,008 rows).
    *   *Columns*: province_code, province, area_no, party_no, party, vote_score.
*   **`summary_winners`**: A summary of the final constituency winners by district (387 rows).
    *   *Columns*: province_code, province, area_no, winner_name, party, score, good_votes, eligible_voters, actual_voters.

## How To Query The Data

You can use standard SQL to query the results! For example, using the `sqlite3` CLI:

```bash
sqlite3 election_2569.db "SELECT province, area_no, winner_name, party FROM summary_winners LIMIT 5;"
```

Or write your own Python scripts to connect and visualize the database using libraries like `sqlite3`, `pandas`, `matplotlib`, or `streamlit`.
