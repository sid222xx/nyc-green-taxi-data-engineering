# NYC Green Taxi Data Engineering Project

## Project Overview

An end-to-end data engineering project built using NYC Green Taxi trip data for 2023. The project demonstrates data ingestion, cloud storage, data transformation and analytical data preparation using Azure Data Factory, Azure Data Lake Storage Gen2 and Azure Databricks.

The project follows the Medallion Architecture: Bronze, Silver and Gold.

## Architecture

```text
NYC Green Taxi Trip Data (2023)
             |
             v
     Azure Data Factory
       (Copy Pipeline)
             |
             v
     Azure Data Lake Gen2
        Bronze Layer
        (Parquet)
             |
             v
      Azure Databricks
          PySpark
             |
             v
        Silver Layer
   Cleaning and Transformation
             |
             v
         Gold Layer
    Aggregations and Analytics
             |
             v
      Databricks Visualizations
```

## Technology Stack

| Technology | Purpose |
|---|---|
| Azure Data Factory | Data ingestion |
| Azure Data Lake Storage Gen2 | Cloud data storage |
| Azure Databricks | Data processing |
| PySpark | Data transformation |
| Delta Lake | Gold-layer table storage |
| SQL | Data analysis |
| Git and GitHub | Version control |

## Project Workflow

### 1. Bronze Layer – Data Ingestion

- Used Azure Data Factory to ingest NYC Green Taxi monthly Parquet files.
- Implemented a parameterized pipeline using a ForEach activity.
- Used an If Condition to handle different monthly source URL patterns.
- Stored the raw data in the Bronze container in Azure Data Lake Storage Gen2.

### 2. Silver Layer – Data Transformation

- Read Bronze data into Databricks using PySpark.
- Applied data cleaning and validation.
- Removed duplicate records.
- Handled null values and invalid trip records.
- Prepared the cleaned data for analytical processing.

### 3. Gold Layer – Analytics

- Created analytical datasets and aggregations using PySpark.
- Prepared Gold-layer outputs for reporting and analysis.
- Used Databricks notebook visualizations to explore the processed data.

## Repository Structure

- `azure-data-factory/` – Azure Data Factory ARM templates.
- `databricks/silver/` – Silver-layer notebook.
- `databricks/gold/` – Gold-layer notebook.
- `documentation/` – Architecture and setup documentation.
- `screenshots/` – Project implementation screenshots.

## Dataset

NYC Taxi and Limousine Commission – Green Taxi Trip Records.

Dataset source: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

## How to Use This Repository

1. Review the Azure Data Factory ARM templates.
2. Configure the required Azure Data Lake Storage connection securely.
3. Deploy or recreate the ADF ingestion pipeline.
4. Configure Databricks access to the Bronze data.
5. Run the Silver notebook.
6. Run the Gold notebook after the Silver data is available.

Refer to the `documentation/` folder for additional details.

## Security

Cloud credentials, storage account keys, passwords and other secrets must not be committed to this repository. Configure credentials separately using secure services such as Azure Key Vault.

## Project Status

The repository contains the ADF deployment artifacts and Databricks Silver and Gold notebooks. Additional reporting or orchestration components should only be considered complete when implemented and tested.