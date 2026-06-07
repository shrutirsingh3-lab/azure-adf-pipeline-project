# 🚀 Azure End-to-End Data Pipeline Project

## 📌 Project Overview
This project demonstrates an end-to-end data pipeline using Azure services. The goal is to move raw CSV data into a structured SQL database using Azure Data Factory and perform basic analysis.

---

## 📂 Dataset
- Source file: diwali_sales.csv`
- Data contains sales information such as:
  - Order ID
  - Product Name
  - Category
  - Amount
  - Order Date

---

## 🏗️ Architecture Flow

CSV File → Azure Blob Storage → Azure Data Factory → Azure SQL Database

---

## ⚙️ Steps Performed

### 1. Resource Creation
- Created Azure Resource Group
- Created Storage Account (Blob Storage)
- Created SQL Server
- Created SQL Database
- Created SQL Table

---

### 2. Data Storage (Raw Layer)
- Uploaded CSV file into Blob Storage container (`raw-data`)

---

### 3. SQL Setup
- Created database
- Created table: `dbo.sales_raw`

---

### 4. Azure Data Factory (ADF)
- Created Data Factory instance
- Created Linked Services:
  - Blob Storage connection
  - SQL Database connection

---

### 5. Pipeline Creation
- Created Copy Data pipeline
- Source: Blob Storage CSV file
- Sink: Azure SQL Database table

---

### 6. Execution
- Triggered pipeline using Debug/Publish
- Verified data loaded successfully into SQL database

---

## 🧪 SQL Analysis Performed

### Basic Queries:
```sql
SELECT COUNT(*) FROM dbo_sales_raw;

SELECT TOP 10 * dbo_sales_raw;

📊 Results
Data successfully moved from raw CSV to structured SQL table
Basic validation and cleaning performed using SQL

🛠️ Tools Used
Azure Blob Storage
Azure Data Factory
Azure SQL Database
SQL Server Query Editor

📌 Key Learning
End-to-end ETL pipeline
Data ingestion using ADF
Source to sink mapping
Basic SQL data validation and cleaning


                ┌────────────────────────────┐
                │   CSV FILE (Dataset)       │
                │  processed_diwali_sales.csv│
                └────────────┬───────────────┘
                             │
                             ▼
        ┌────────────────────────────────────┐
        │   AZURE BLOB STORAGE (RAW LAYER)   │
        │   Container: raw-data             │
        └────────────┬──────────────────────┘
                             │
                             │ (Linked Service)
                             ▼
        ┌────────────────────────────────────┐
        │  AZURE DATA FACTORY (ADF)         │
        │  - Pipeline (Copy Activity)       │
        │  - Source: Blob Storage           │
        │  - Sink: SQL Database             │
        └────────────┬──────────────────────┘
                             │
                             │ (Linked Service)
                             ▼
        ┌────────────────────────────────────┐
        │  AZURE SQL DATABASE                │
        │  Database: retail_db              │
        │  Table: processed_diwali_sales    │
        └────────────────────────────────────┘
