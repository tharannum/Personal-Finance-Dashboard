# Personal-Finance-Dashboard

## 1. Project Overview
This project involves the development of a comprehensive Personal Finance Dashboard using Power BI. It transforms raw financial transaction data into an interactive visual tool that allows users to track income, expenses, savings, and financial targets over time. The dashboard provides a holistic view of personal financial health, enabling data-driven decisions for better money management.

## 2. Business Problem
Managing personal finances can be complex due to scattered data across various transaction types (income, expenses, savings). Without a centralised view, it is difficult to:
* Track monthly growth in savings or income.
* Identify spending patterns across different categories (e.g., House Rent, Groceries, Leisure).
* Monitor progress against financial targets (e.g., saving 25% of income).
* Understand the "Month-over-Month" (MoM) changes in financial status.

## 3. Goal of the Dashboard
The primary goal is to create an intuitive, interactive dashboard that:
* **Consolidates Data:** Brings together Income, Expense, and Savings data into a single view.
*  **Visualizes Trends:** Shows financial performance over time (2021-2024).
*  **Enables Analysis:** Allows deep dives into specific financial components (e.g., "Mutual Funds" vs. "Liquid Cash").
*  **Tracks Targets:** Monitors actual savings against a set target percentage.

## 4. Data Description

### Source
* **Data Format:** The raw data was sourced from an Excel/CSV file ("Finance Dataset.xlsx - FinData.csv") containing transaction records.
* **Structure:** The original dataset is in a wide format with columns for `Type` (Income, Expense, Savings, Target), `Component` (e.g., Salary, House Rent), and date columns for each month (e.g., 2021-01-01, 2021-02-01).

### Data Cleaning & Modeling (Power Query)
* **Unpivoting:** The wide date columns were unpivoted to create a streamlined structure with `Date` and `Value` columns, making the data suitable for time-series analysis.
* **Table Schema:** The final data model includes:
    * **Fact Table (`Dataset`):** Contains `Type`, `Component`, `Date`, `Value`, `Year`, and `Month_Yr`.
    * **Date Table (`Selected_Date`):** Created using DAX to handle time intelligence functions.
    * **Selection Table (`Line_selection_Table`):** A disconnected table created to allow dynamic metric selection in charts (Income, Savings, Expenses, Target).

## 5. Analysis Performed

### DAX Calculations
Key measures were created to drive the dashboard's interactivity and insights:
* **Dynamic Title:** Changes based on the selected metric (e.g., "Income by Date").
* **Core Metrics:**
    * `Total_Value`: Sum of values.
    * Income`, `Expenses`, `Savings`: Filtered calculations based on the 'Type' column.
* **Ratios & Growth:**
    *  `Saving%`: Savings divided by Income.
    *  `Expense%`: Expenses divided by Income.
    *  `Ex_Vs_Sav`: Ratio of Savings to Expenses.
    *  `Income Change MoM%`: Month-over-Month income growth.
    *  `Monthly_Growth`: Comparison of current vs. previous year monthly sales/values.
*  **Dynamic Visual Switching:** A `SWITCH` function (`Line_chart_measure`) allows the main chart to toggle between displaying Expense%, Income Change, Saving%, or Target based on user selection.
## Overview of Dashboard 
![Dashboard](https://github.com/tharannum/Personal-Finance-Dashboard/blob/main/financial%20dashboard%20.jpg)

## 6. Feature Highlights & Walkthrough of Key Visuals

### 1. **KPI Cards (Top Right)**
*  **Overview:** Display high-level totals for Income (3M), Expenses (1M), and Savings (2M) 
*  **Growth Indicators:** Show monthly percentage changes (e.g., Income up 9.84%, Expenses up 45.53%) to give immediate context on recent performance.
*  **Ratios:** Display crucial financial health ratios like "Saving%" (64%) and "Ex_Vs_Sav" (140.45%).
### 2. **Dynamic Trend Chart (Main Visual)**
* **Function:** A large area chart showing the trend of the selected metric over time (2021-2024).
*  **Interactivity:** Users can click tabs (Expenses, Income, Savings, Target) to dynamically change the metric displayed on the Y-axis, powered by the `Line_selection_Table` .

### 3. **Donut Charts (Bottom Left & Center)**
* **Expenses Breakdown:** Visualizes the distribution of spending across categories like House Rent, Groceries, and EMIs.
*  **Savings Breakdown:** Shows where savings are allocated, such as Liquid Cash, Mutual Funds, or Fixed Deposits.

### 4. **Matrix View (Bottom Right)**
* **Detailed Table:** Provides a granular view of financial data, hierarchically organized by `Target`, `Savings`, `Income`, and `Expense`.
*  **Yearly Comparison:** Columns allow easy comparison of values across years (2021 vs. 2022).

### 5. **Slicers**
*   **Date Selection:** Allows filtering data by specific years (2021, 2022, 2023, 2024) or months (e.g., Sep-21) to narrow the analysis scope .

## 7. Business Questions Answered
*  **"How has my income grown month-over-month?"** (Answered by `Income Change MoM%`)
*  **"Am I meeting my savings target of 25%?"** (Answered by `Target` vs `Saving%` metrics).
* **"What is my biggest expense category?"** (Answered by the Expenses Donut Chart).
* **"How does my saving compare to my expenses?"** (Answered by the `Ex_Vs_Sav` ratio).

## 8. Insights & Business Impact
*  **High Savings Rate:** The dashboard reveals a healthy financial status with a 64% savings rate and a high Savings-to-Expense ratio (140%).
*  **Expense Control:** Visualising expenses helps identify that "House Rent" and "Groceries" are major cost drivers, allowing for targeted budgeting.
* **Income Stability:** The trend lines and KPI cards allow users to instantly spot dips in income or spikes in expenses, enabling proactive financial adjustments.
  

## 9. Recommendations
*  **Invest Surplus:** With a high "Liquid Cash" portion in savings , the user should consider diverting more funds into high-yield investments like "Mutual Funds" to beat inflation.
*  **Monitor "Other" Expenses:** Use the granular matrix view to audit the "Other" expense category  to ensure miscellaneous spending isn't "leaking" money.
*  **Set Dynamic Targets:** Adjust the static "Target"  to be dynamic based on income brackets (e.g., higher savings target for higher income months).

## 10. Skills Used
* **Data Transformation:** Power Query (Unpivoting, Formatting).
* **Data Modeling:** Star Schema design, Date Tables.
* **DAX:** `CALCULATE`, `DIVIDE`, `SELECTEDVALUE`, `SWITCH`, Time Intelligence (`DATEADD`, `PREVIOUSMONTH`).
* **Data Visualization:** Custom Tooltips, Dynamic Titles, KPI Cards, Drill-throughs.
 
