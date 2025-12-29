# Sales Insights Data Analysis Project

## 📌 Project Overview
This project focuses on analyzing sales data to extract meaningful business insights using **SQL** and **Power BI**. The objective is to help stakeholders understand revenue trends, market performance, and customer behavior through structured queries and interactive dashboards.

The project simulates a real-world sales analytics workflow, starting from raw database extraction to visualization-driven decision support.

---

## 🛠 Tools & Technologies
- **MySQL** – Data storage and querying  
- **SQL** – Data analysis and aggregation  
- **Power BI** – Interactive dashboards and visualizations  
- **Git & GitHub** – Version control and project hosting  

---

## 📂 Dataset Description
The dataset is provided as a MySQL database dump.

**File included:**
- `db_dump.sql`

**Key tables:**
- `customers`
- `transactions`
- `markets`
- `date`

The data contains information about customer purchases, sales amounts, currencies, dates, and market locations.

---

## ⚙️ Setup Instructions

### 1️⃣ Install MySQL
Follow this tutorial to install MySQL on your system:  
👉 https://www.youtube.com/watch?v=WuBcTJnIuzo

### 2️⃣ Import Database
- Download `db_dump.sql`
- Import it into MySQL using MySQL Workbench or command line

### 3️⃣ Run SQL Queries
Execute the provided SQL queries to explore and analyze the dataset.

### 4️⃣ Open Power BI Dashboard
- Open `sales_insights_analysis.pbix` using Power BI Desktop
- Refresh data if required

---

## 📊 SQL Analysis Examples

```sql
-- Show all customers
SELECT * FROM customers;

-- Count total customers
SELECT COUNT(*) FROM customers;

-- Transactions from Chennai market
SELECT * FROM transactions WHERE market_code = 'Mark001';

-- Distinct products sold in Chennai
SELECT DISTINCT product_code 
FROM transactions 
WHERE market_code = 'Mark001';

-- Total revenue in 2020
SELECT SUM(transactions.sales_amount)
FROM transactions
INNER JOIN date ON transactions.order_date = date.date
WHERE date.year = 2020;
```

---

## 📈 Power BI Dashboard Features
- Revenue analysis by market
- Year-wise and month-wise sales trends
- Top-performing customers and products
- Currency normalization for accurate revenue comparison

### Currency Normalization Formula
```powerquery
= Table.AddColumn(
    #"Filtered Rows",
    "norm_amount",
    each if [currency] = "USD" or [currency] = "USD#(cr)" 
    then [sales_amount] * 75 
    else [sales_amount],
    type any
)
```

---

## 🎯 Key Insights
- The business generated a **total revenue of ₹985M** with approximately **2M units sold**, but the **overall profit margin is only ~2.5%**, indicating thin profitability.
- **Delhi NCR** is the strongest market, contributing **over 50% of total revenue** and nearly **49% of total profit**.
- **Bengaluru shows a major loss (-20.8% profit contribution)**, despite sales activity.
- Several markets generate revenue but contribute **low or negative profit**, emphasizing the need for profit-focused strategies.
- Revenue peaked in **2018** and declined towards **2020**.
- Sales are dependent on a **small group of customers and products**, increasing concentration risk.
- Currency normalization ensured accurate cross-market revenue comparison.

---

## 📎 Project Files
- `db_dump.sql` – MySQL database dump  
- `sales_insights_analysis.pbix` – Power BI dashboard  
- `README.md` – Project documentation  

---

## 🚀 Future Enhancements
- Automate data cleaning using Python
- Add predictive sales forecasting
- Integrate live database connection with Power BI
- Publish dashboard using Power BI Service

---

## 👤 Author
**Durga Prasad**  
Data Science Student  

- 📧 Email: prasadshetty1275@gmail.com  
- 🔗 LinkedIn: https://www.linkedin.com/in/durgaprasadshetty
