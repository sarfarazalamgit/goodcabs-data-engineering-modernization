# GoodCabs Data Engineering Modernization

**Transforming GoodCabs' Regional Data Analytics through Databricks Lakehouse and Declarative Spark Pipelines**

---

## Table of Contents
- [Problem Statement](#problem-statement)
- [Solution Approach](#solution-approach)
- [Key Improvements](#key-improvements)
- [Project Objectives](#project-objectives)
- [Project Architecture](#project-architecture)
- [Datasets](#datasets)
- [Code Repository](#code-repository)
- [ETL Pipeline Overview](#etl-pipeline-overview)
- [Setup Instructions](#setup-instructions)
- [Environment Configuration](#environment-configuration)
- [Data Pipeline Management](#data-pipeline-management)

---

## Problem Statement

**Company:** GoodCabs (**Fast-growing Cab Service Company**)

**Key Challenges:**
- **Delayed Regional Data Delivery**
- **Generic, Hard-to-Use Dashboards**
- **Manual Data Export and Reworking**
- **Slow Innovation Cycles**
- **Procedural Spark Pipelines with Manual Orchestration**
- **Tightly Coupled Data Processing Systems**

---

## Solution Approach

### Technology Stack
- **Platform:** **Databricks**
- **Data Processing:** **Lakehouse Architecture**
- **Pipeline Approach:** **Declarative Spark Pipelines (LakeFlow)**

### Key Improvements
- **Declarative Data Intent Specification**
- **Automated Execution Plan Optimization**
- **Efficient Dependency Management**
- **Scalable Incremental Processing**
- **Faster Regional Data Insights**

---

## Project Objectives

### 1. Operational Efficiency
- **Reduce Data Delivery Time**
- **Develop Region-Specific, Actionable Dashboards**
- **Minimize Manual Data Manipulation**

### 2. Technical Modernization
- **Transition from Procedural to Declarative Data Pipelines**
- **Enhance Data Platform Flexibility**
- **Enable Rapid Adaptation to Regional Needs**

---

## Project Architecture

![Project Architecture](https://github.com/sarfarazalamgit/goodcabs-data-engineering-modernization/blob/main/architecture.png?raw=true)

---

## Datasets

- [Data Files](https://github.com/sarfarazalamgit/goodcabs-data-engineering-modernization/tree/main/1.%20data)

---

## Code Repository

- [Code Files](https://github.com/sarfarazalamgit/goodcabs-data-engineering-modernization/tree/main/2.%20codes)

---

## ETL Pipeline Overview

### Data Layers

#### **Bronze Layer**
- **Purpose:** Raw data ingestion.
- **Components:**
  - `city.py`: Ingests city data from `city.csv` into the bronze table.
  - `trips.py`: Ingests trip data from `trip_export.csv` into the bronze table.

#### **Silver Layer**
- **Purpose:** Transformation and cleaning of raw data for analytics.
- **Components:**
  - `calendar.py`: Generates a comprehensive calendar dimension.
  - `city.py`: Cleans and standardizes city data.
  - `trips.py`: Processes trip data applying validations and transformations.

#### **Gold Layer**
- **Purpose:** Refined analytical layer containing aggregated data.
- **Components:**
  - `trips_gold.sql`: Consolidates trip data.
  - Localization SQL scripts (e.g., `trips_coimbatore.sql`, `trips_indore.sql`): Enables localized analysis.

---

## Setup Instructions

To set up and run the GoodCabs data engineering project using Databricks Spark Declarative Pipelines (LakeFlow), follow these steps:

### Prerequisites
- **Databricks Account:** Create one [here](https://databricks.com/).

### Step-by-Step Setup

1. **Clone the Repository**
   - Clone the repository using Databricks Repos:
   ```bash
   git clone https://github.com/sarfarazalamgit/goodcabs-data-engineering-modernization.git

2. **Create a New Cluster**
   - In your Databricks workspace, create a new cluster by navigating to the **Clusters** section.
   - Configure the cluster with the recommended specifications and any necessary libraries required for the project.

3. **Upload Data Files**
   - Navigate to the **Data** section in Databricks.
   - Upload the `city.csv` and `trip_export.csv` files directly into your workspace.

4. **Create Notebooks for Each File**
   - For **Python Scripts**: Create separate notebooks for:
     - `trips.py`
     - `city.py`
     - `calendar.py`
   - For **SQL Scripts**: Create separate notebooks for:
     - `trips_gold.sql`
     - `trips_coimbatore.sql`
     - `trips_indore.sql`
     - (Add more as necessary for other regions)

5. **Copy Code into Notebooks**
   - Open each corresponding notebook and copy the contents from the respective `.py` and `.sql` files into the notebooks.

6. **Set Up the Bronze Tables**
   - Ensure that the bronze tables (`transportation.bronze.trips` and `transportation.bronze.city`) are populated with data from your CSV files.
   - This can be done by executing the Python scripts to read the CSV data and create the respective tables.

7. **Run the Data Pipelines**
   - Start by executing the notebook for `city.py` to create the silver layer for cities.
   - Next, run `trips.py` to create the silver layer for trips.
   - Then, execute `calendar.py` to generate the calendar dimension.
   - Finally, run `trips_gold.sql` to create the gold fact table.

8. **Execute Regional Queries**
   - Use the regional SQL scripts like `trips_coimbatore.sql` to filter and analyze trip data specific to those locations.

9. **Review Results**
   - Check the created tables and views within the Databricks SQL interface to ensure that everything runs correctly.
   - Utilize dashboards or perform SQL queries to explore the processed data.

---

## Environment Configuration
- Set the necessary Spark configurations, such as `start_date` and `end_date`, required in scripts. This can be done through the cluster configuration settings or directly within the notebooks.

---

## Data Pipeline Management
- Utilize the declarative features of LakeFlow to manage data workflows effectively. This will allow for easier modifications in the future and enhance the adaptability of your data processing pipelines.

---

