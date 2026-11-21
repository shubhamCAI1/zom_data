# Zomato Bangalore Restaurants Data Cleaning & Preprocessing

## Project Overview
This repository contains a Google Colab / Jupyter Notebook (`DataAnalytics_proj1.ipynb`) focused on cleaning and preprocessing the **Zomato Bangalore Restaurants** dataset (`zomato.csv`). The raw dataset contains **51,717 records** across **17 columns**, and this workflow prepares the data for downstream exploratory data analysis (EDA), business intelligence dashboards (Power BI / Tableau), and machine learning tasks.

## Folder Structure
Based on the repository layout:
```text
zom_data/
├── Notebooks/          # Jupyter/Colab notebooks (DataAnalytics_proj1.ipynb)
├── PBI/                # Power BI dashboard files
├── Python/             # Python scripts
├── Tableau/            # Tableau workbook files
├── README.md           # Project documentation
└── requirements.txt    # Python dependencies
```

## Data Cleaning Workflow
The notebook performs the following preprocessing steps on the raw dataset:

1. **Data Ingestion:**
   - Mounts Google Drive in Google Colab and loads `zomato.csv` using `pandas`.
2. **Feature Selection (Dropping Irrelevant Columns):**
   - Drops columns not required for downstream analysis: `url`, `address`, `name`, `phone`, `book_table`, and `listed_in(city)`, reducing the dataset from 17 to 11 columns.
3. **Deduplication:**
   - Identifies and removes duplicate entries, reducing the dataset from **51,717** rows to **41,763** unique records.
4. **Handling Missing Values:**
   - Drops rows with missing `location` entries (leaving **41,759** rows).
   - Imputes missing values in `cuisines` and `rest_type` with `'unknown'`.
5. **Data Type Conversion & Imputation:**
   - Renames `approx_cost(for two people)` to `cost_per_two`.
   - Removes comma formatting (e.g., `'1,500'` $\rightarrow$ `1500`), converts values to numeric types, and imputes missing entries using the column mean.
6. **In Progress:**
   - Parsing and cleaning the `rate` column (e.g., extracting numeric ratings from `'4.1/5'` strings).

## Getting Started

### Prerequisites
- Python 3.8+
- Google Colab or a local Jupyter Notebook environment

### Installation
1. Clone the repository:
   ```bash
   git clone <your-repository-url>
   cd zom_data
   ```
2. Install the required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```

### Usage
- **In Google Colab:** Upload `DataAnalytics_proj1.ipynb`, place `zomato.csv` in your Google Drive, update the file path in the `pd.read_csv()` cell if needed, and run all cells.
- **Locally:** Replace `drive.mount('/content/drive')` with a local file path to `zomato.csv` and run the notebook via Jupyter Notebook or VS Code.