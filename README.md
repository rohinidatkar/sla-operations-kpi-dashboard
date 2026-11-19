# SLA and Operations KPI Dashboard

Measures how well a support team meets its Service Level Agreements (SLAs), shows where breaches concentrate, and flags open tickets at risk of breaching. SQL does the KPI logic; the output feeds a Power BI dashboard.

> **Dataset:** synthetic (5,000 tickets, fixed random seed), generated inside the notebook so the project is reproducible and uses no confidential data. SLA targets: Critical 4h, High 8h, Medium 24h, Low 48h.

## Business questions
1. What percentage of tickets are resolved within SLA, overall and by priority and category?
2. Where do SLA breaches concentrate?
3. Which open tickets need follow-up right now?

## Tools
SQL (SQLite) | Python (Pandas, Matplotlib) | Power BI

## Key results (from this dataset)
- Overall SLA compliance: **60.4%** (1,956 breaches out of 4,941 resolved tickets); average resolution time 25.2 hours.
- Lowest compliance by priority: **Low** (57.3%).
- Lowest compliance by category: **Hardware** (43.3%).
- Highest breach-rate combination: **Low / Hardware** (59.4%).
- Open tickets needing follow-up: **23** (16 already breached, 7 at risk).

## Project structure
```
01-sla-operations-kpi-dashboard/
|-- sla_kpi_analysis.ipynb      # full analysis (SQL + Python)
|-- data/tickets.csv            # generated ticket data
|-- output/                     # CSVs prepared for Power BI
|   |-- powerbi_tickets.csv
|   |-- kpi_by_priority.csv
|   |-- kpi_by_category.csv
|   `-- open_tickets_at_risk.csv
`-- screenshots/                # add your Power BI dashboard screenshot here
```

## How to run
```bash
pip install -r ../requirements.txt
jupyter notebook sla_kpi_analysis.ipynb
```
Run all cells; the CSV files in `output/` are regenerated.

## Power BI dashboard
Step-by-step build instructions and DAX measures are at the end of the notebook. After building, save a screenshot into `screenshots/` and link it here:

`![Dashboard](screenshots/dashboard.png)`

## Skills demonstrated
SQL (views, aggregation, CASE logic, date arithmetic) | KPI design | Data visualization | Power BI data preparation and DAX
