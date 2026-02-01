# 📊 Credit Score Classification using Databricks 

## 🧠 Problem Statement

Financial institutions rely heavily on **credit scores** to decide whether a customer is eligible for loans, credit cards, and favorable interest rates.  
However, manually evaluating customer financial behavior is **time-consuming, error-prone, and not scalable**.

The goal of this project is to **build an end-to-end credit score classification system** that predicts a customer’s credit score category (**Good, Standard, or Poor**) using historical financial and behavioral data.

This project demonstrates:
- A **modern data engineering pipeline** using the **Databricks Medallion Architecture**
- **Feature engineering** for financial risk modeling
- **Machine learning model training, tuning, and registration**
- **Production-ready governance** using **Unity Catalog**
- **Business insights** via an interactive **Databricks dashboard**

---

## 🎯 Project Objectives

- Build a **scalable data pipeline** from raw data to ML-ready features  
- Clean and standardize **real-world noisy financial data**
- Engineer **gold-level features** for credit risk prediction
- Train and tune **classification models**
- Register models using **MLflow**
- Visualize insights using **Databricks dashboards**

---

## 📂 Dataset Overview

- **Source**: Kaggle (US Credit Score Dataset)
- **Type**: Customer-level financial and credit behavior data
- **Records**: Monthly records for multiple customers
- **Target Variable**: `Credit_Score` (Good / Standard / Poor)
- **Total Columns**: 28
- **Time Span**: January to August (multiple months per customer)

The dataset contains **demographic, income, debt, payment behavior, and credit usage information**.

---

## 🧱 Data Architecture (Medallion Architecture)

<img width="1114" height="805" alt="image" src="https://github.com/user-attachments/assets/9b3ba54d-0676-4bd4-a349-0ada5e44d0eb" />



This project follows the **Databricks Medallion Architecture**:

### 🟤 Bronze Layer (Raw Data)
- Raw data ingested from Kaggle
- Minimal transformations
- Stored in:  
  `credit_catalog.bronze`

### ⚪ Silver Layer (Cleaned & Standardized)
- Data cleaning and validation
- Handling missing values and corrupted records
- Removing redundant columns
- Standardizing data types
- ML-specific feature engineering
- Stored in:  
  `credit_catalog.silver`

### 🟡 Gold Layer (Business & ML Ready)
- Aggregated features for analysis
- Removal of Collinear Features
- Stored in:  
  `credit_catalog.gold`

---

## 🔁 End-to-End Pipeline Flow

1. **Data Ingestion**
   - Download data from Kaggle
   - Store raw files in **Unity Catalog volume**
   - Notebook: `Data_Ingestion`

2. **Bronze Processing**
   - Load raw data into Delta tables
   - No heavy transformations

3. **Silver Processing**
   - Data cleaning and validation
   - Handle invalid values (negative age, corrupted strings, outliers)
   - Drop non-useful columns (e.g., Month for classification)

4. **Gold Processing**
   - Aggregation features 
   - ML features for prediction

5. **Machine Learning**
   - Model selection
   - Hyperparameter tuning
   - Model training
   - Model registry using MLflow

6. **Visualization**
   - Business insights dashboard on Databricks

---

## 🧪 Feature Engineering (Silver Layer)

Examples of engineered features:
- EMI to income ratio
- Debt to income ratio
- Splits payment behaviour into spending behaviour and payment value
- saving capacity
- Payment behavior 
- Income group based on GNI per capita thresholds.

These features are optimized for **credit risk prediction**.

---

## 🤖 Machine Learning Workflow

### Model Type
- **Classification** (Multi-class)

### Steps
- Train-test split
- Feature scaling (where required)
- Model comparison
- Hyperparameter tuning using **Optuna**
- Final model training
- Experiment tracking using **MLflow**
- Model registration in Databricks Model Registry

### Algorithms Used
- XGBoost
- Tree-based models (best suited for tabular financial data)

---
## 📈 Model Performance (Test Dataset)
- **Accuracy:** 0.80
- **Macro F1-Score:** 0.79
- **roc_auc_score:** 0.92


## 📊 Dashboard & Insights

An interactive **Databricks dashboard** was created to visualize:
- Credit score distribution
- Income vs credit score
- Debt and EMI patterns
- Credit utilization behavior
- Customer segmentation insights

This helps translate **technical results into business-friendly insights**.

---

## 🗂️ Project Folder Structure

```text
Credit-Score-Prediction/
├── script/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── ml/
│   ├── model_selection.ipynb
│   ├── model_training.ipynb
│   └── model_registry.ipynb
│
└── admin/
    └── unity_catalog_governance.sql

```
## 🛠️ Tech Stack

### 🔹 Programming & Query Languages
- **Python** - Core programming language for data processing and ML
- **SQL** - Data querying, aggregation, and governance

### 🔹 Big Data & Cloud Platform
- **Databricks** - Unified analytics platform
- **Apache Spark (PySpark)** - Distributed data processing
- **Delta Lake** - Reliable storage with ACID transactions

### 🔹 Machine Learning & Modeling
- **Scikit-learn** - Baseline ML models and preprocessing
- **XGBoost** - High-performance gradient boosting for classification
- **Optuna** - Hyperparameter optimization

### 🔹 Experiment Tracking & Model Management
- **MLflow** - Experiment tracking, model registry, and lifecycle management

### 🔹 Data Governance & Security
- **Unity Catalog** - Centralized governance, access control, and metadata management

### 🔹 Visualization
- **Databricks Dashboards** - Business insights and analytical reporting


## 👨‍💻 Author

**Sourav Raj**  
Data Scientist | Data Analyst & ML Enthusiast  
Built with ❤️ using Databricks

Feel free to connect on LinkedIn or explore my other projects.

🔗 LinkedIn: https://www.linkedin.com/in/sourav664


