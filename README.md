# Sales-Analytics-Using-Azure-Databricks


**Porject Overview**

This project demonstrates an end-to-end Retail Sales Data Analytics workflow, beginning with cloud environment setup and progressing through data ingestion, data-quality assessment, evidence-based cleaning, Delta Lake storage, version-controlled development, and local analytical continuation.

The project was initially developed using Microsoft Azure, Azure Data Lake Storage Gen2, Azure Databricks, PySpark and Delta Lake. Following the Databricks environment being discontinued, the persisted analytical data and source code were retained and the project is being continued locally using VS Code, Python and SQL-oriented analytical tools.

The project addresses the following business question:
What product and outlet characteristics are associated with stronger sales performance, and where are the key opportunities for improving retail performance?

Rather than applying generic cleaning rules, the project uses evidence-based data-quality investigation to determine which values should be corrected, retained, or removed. The cleaned dataset is then analysed using SQL with DuckDB to identify outlet performance patterns and potential business opportunities.

The project focuses on Data Analytics and diagnostic reasoning rather than Machine Learning.


**Business Objective**

The retail organisation operates across multiple outlets and sells a range of products. Sales performance varies across outlets and product categories.

The analysis aims to understand:
- Where sales performance is strongest and weakest
- Whether unusual data values represent genuine observations or data-quality problems
- Which outlet and product patterns are associated with stronger sales
- Whether high-performing outlets provide useful benchmarks for lower-performing outlets
- Which findings are strong enough to support business investigation without making unsupported causal claims.


**Technology Stack**

Cloud & Data Processing
- Microsoft Azure
- Azure Data Lake Storage Gen2
- Azure Databricks
- PySpark
- Delta Lake

Local Analytics
- Python
- Pandas
- DuckDB
- SQL

Development & Version Control
- Visual Studio Code
- Jupyter Notebook
- Git
- GitHub


**Project Architecture**

**Phase 1:**

Cloud Processing Stage

Raw Sales Data -> Azure Data Lake Storage -> Azure Databricks -> PySpark (Data Quality Assessment, Data Cleaning) -> Cleaned Dataset -> Delta Lake


**Phase 2:**

Local Analytical Stage 

Persisted Cleaned Data -> VS Code / Python -> PySpark to Pandas (Data Reading) -> DuckDB / SQL (Data Quality Assessment) -> Business Analysis -> Findings & Business Direction


**Key Findings**

| Area | Finding | Decision / Implication |
|---|---|---|
| Item Weight | Missing values were recoverable for most affected items using consistent item-level evidence | Recover where reliable evidence existed |
| Unrecoverable Records | 4 records, approximately 0.05%, could not be reliably recovered | Removed to maintain analytical completeness |
| Item Visibility | 526 records, 6.17%, had zero visibility | Investigated rather than automatically imputed |
| Zero Visibility Sales | Approximately 6.3% of sales came from zero-visibility records | Zero values were retained |
| Zero Visibility Mean | Average sales were approximately 2% higher | Mean alone was insufficient evidence of an error |
| Zero Visibility Median | Median sales were slightly lower | Distribution did not support blanket imputation |
| Outlet Performance | OUT027 recorded approximately 369,578 in total sales | Use as a benchmark for further investigation |
| Outlet Gap | OUT027 was approximately 51.5% above OUT035 | Investigate differences between stronger and weaker outlets |
| OUT027 Visibility | Zero- and non-zero-visibility records had almost identical average sales | Visibility alone does not explain OUT027's performance |


**Repository Structure**

"""
Sales-Analytics-Using-Azure-Databricks/
├── .gitignore
├── DeltaLake.ipynb
├── README.md
├── Utkarsh_Sales Project.ipynb
└── notebook/
    ├── data_analysis.ipynb
    ├── data_quality_investigation.ipynb
    └── sales_performance.ipynb
"""