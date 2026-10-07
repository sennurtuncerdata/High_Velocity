#  AML Transaction Monitoring: Velocity & Volume Spike Analytics

A hybrid **SQL (DuckDB) & Python (Pandas)** data analytics project designed to identify high-risk financial transaction volume spikes and velocity anomalies in large-scale banking data (PaySim Dataset).

---

##  Project Overview

In Anti-Money Laundering (AML) transaction monitoring, sudden and significant spikes in transaction volume or velocity are critical red flags for potential money laundering, fraud, or account takeover. 

This project implements a **two-tier monitoring strategy**:
1. **High-Performance Filtering (DuckDB / SQL):** Scans multi-million row transaction datasets to compute historical baselines and flag extreme volume anomalies.
2. **Behavioral Risk Segmentation (Pandas):** Categorizes flagged accounts into risk tiers (`HIGH_VELOCITY_RISK`, `MEDIUM_VELOCITY_RISK`) and generates prioritized manual review queues for compliance analysts.

---

##  Tech Stack & Libraries

* **Database Engine:** DuckDB (In-memory OLAP SQL engine for fast execution over CSV data)
* **Data Manipulation & Analysis:** Python, Pandas, NumPy
* **Interactive Environment:** Jupyter Lab / Jupyter Notebook (`IPython.display`)
* **Dataset:** PaySim Synthetic Financial Datasets

---

##  AML Logic & Methodology

### Key Metrics Defined
* **`total_amount_last_48h`**: Cumulative transfer volume produced by the customer.
* **`baseline_daily_volume`**: System-wide expected baseline volume derived from historical daily activity.
* **`spike_multiplier`**: Ratio showing how many times the transaction volume exceeds the standard daily baseline.
* **`manual_review_flag`**: Automated priority label (`HIGH_PRIORITY_REVIEW` vs `STANDARD_REVIEW`) passed to compliance teams.

---

## Sample Output & Risk Breakdown
The notebook outputs clean HTML tables detailing risk distribution and top prioritized cases:
Risk Distribution: Aggregated statistics showing alert counts, average transfer amounts, and maximum spike multipliers per risk tier.
Top Velocity Cases: Identified single-transaction large-volume spikes (e.g., transfers over $90M representing 14x–21x baseline multipliers).
AML Review Candidates: A structured table optimized for L1/L2 AML Compliance Analysts to begin manual SAR (Suspicious Activity Report) investigations.
 Business Impact & Value
Reduced False Positives: By establishing data-driven baseline multipliers, only truly anomalous transactions are pushed to analysts.
Scalable Architecture: Utilizing DuckDB enables fast SQL analytical queries directly on local CSVs without requiring heavy database infrastructure.
Operational Efficiency: Automated prioritization (HIGH_PRIORITY_REVIEW) ensures compliance teams address high-impact financial risk first.



```bash
pip install duckdb pandas numpy jupyterlab
