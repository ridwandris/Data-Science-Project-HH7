# The German Housing Market: Where Are Prices Heading?

**Analysis and Forecast of Owner-Occupied Housing Price Indices (2010–2024)**  
*Data Science Group 7 – TechLabs Hamburg*

---

## Problem Statement:
Our motivation behind this project stems from the sharp rise in housing prices and the fact that buying a home is increasingly only possible through loans, we were motivated to explore how housing costs have changed over time in Germany. We aim to analyze and forecast the development of owner-occupied housing price indices in Germany from 2010 to 2024 using time series models and economic indicators. As young adults, this is also a personal concern, as affording property has become a growing challenge for our generation.
We want to understand the factors driving these price changes and provide insights into future trends, which could be valuable for potential homeowners, investors, and policymakers.

Our main research question is:  
 *“Where are prices heading?”*

---

## Objectives
- Analyze housing price developments in Germany (2010–2024)  
- Apply **time series models** to forecast future price trends  
- Provide **visualizations** for clear communication  
- Create transparency for public discussion and policymakers  

---

## Data
- **Source:** [Destatis GENESIS Database](https://www-genesis.destatis.de/)  
- **Format:** CSV (flat structure, German notation `;` separator, `,` as decimal)  

---

## Methods & Workflow
Our Jupyter Notebook follows a clear pipeline:  

### Data Import
- Reading CSV with `pandas`  
- Handling German encodings (`cp1252`) and separators (`;`)  
- Replacing missing values (`-`, empty strings)  

```python
df_raw = pd.read_csv(
    DATA_PATH, sep=";", decimal=",", encoding="cp1252", na_values=["-", "", " "]
)
```
### Data Cleaning

Renaming columns (time → year, 1_variable_label → category, value → index_value)

Converting years and index values to numeric

Filtering valid years

### Time Series Analysis

Extracting series by category (e.g. “Deutschland insgesamt”)

Checking for stationarity with ADF Test

Applying ARIMA(p,d,q) models for forecasting

### Forecasting

Model: ARIMA(1,2,1)

Forecast horizon: 3 years (2025–2027)

Results plotted with 95% confidence intervals

### Results
- Housing prices in Germany rose steadily from 2010 to 2024  
- Our ARIMA model predicts continued growth for the next 3 years  
- Forecast uncertainty widens, but trend remains upward  

(*Example plot goes here – you can embed `forecast.png`*)  

---

## How to Run
1. Clone this repository  
   ```bash
   git clone https://github.com/ridwandris/Data-Science-Project-HH7.git

2. Create a virtual environment
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # on macOS/Linux
   .venv\Scripts\activate      # on Windows

3. Install requirements
   ```bash
   pip install -r requirements.txt

4. Open Jupyter Notebook

## Team

This project was created as part of a **TechLabs Data Science project**.  

**Team members:**  
- Claudia Proenza Alegria
- Haydo Bulut
- Mai Phuong Hoang
- Ridwan Iddris

