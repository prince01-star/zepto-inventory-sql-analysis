# 🛒 Zepto Inventory Data Analysis using SQL

## 🚀 Project Overview

This project performs **end-to-end SQL data analysis** on Zepto's product inventory dataset to uncover business insights related to pricing, discounts, stock availability, and revenue potential.

The workflow covers:

✔ Data Exploration  
✔ Data Cleaning  
✔ Feature Transformation  
✔ Business Querying  
✔ Insight Generation  

This mirrors real-world responsibilities of a **Data Analyst** working with retail or quick-commerce datasets.

---

## 🎯 Business Problem

Quick-commerce platforms manage thousands of SKUs across categories. Without structured analysis, it becomes difficult to:

- Identify high-discount products  
- Detect stock risks  
- Estimate inventory revenue  
- Optimize pricing strategies  
- Understand category-level performance  

👉 This project uses SQL to transform raw inventory data into **decision-ready insights**.

---

## 🛠️ Tech Stack

- **SQL (MySQL)**
- Data Cleaning Techniques  
- Aggregations & Grouping  
- CASE Statements  
- Business-Focused Queries  

---

##  Dataset Information

The dataset contains product-level inventory data including:

- Product Name  
- Category  
- MRP  
- Discount Percentage  
- Discounted Selling Price  
- Weight (grams)  
- Available Quantity  
- Stock Status  

---

##  Database Setup

```sql
CREATE DATABASE Zepto;
USE Zepto;
```

Added a primary key for better table structure:

```sql
ALTER TABLE zepto_v2 
ADD COLUMN serial_no INT AUTO_INCREMENT PRIMARY KEY FIRST;
```

---

## 🔎 Data Exploration

Key checks performed:

✅ Row count  
✅ Sample data inspection  
✅ NULL value detection  
✅ Unique categories  
✅ Duplicate product identification  
✅ Stock availability analysis  

Example:

```sql
SELECT DISTINCT category 
FROM zepto_v2
ORDER BY category;
```

---

## 🧹 Data Cleaning

### Removed Invalid Pricing
Products with zero price were deleted to ensure analytical accuracy.

```sql
DELETE FROM zepto_v2 WHERE mrp = 0;
```

### Converted Pricing Units
Prices were converted from **paise to rupees** for realistic business interpretation.

```sql
UPDATE zepto_v2
SET mrp = mrp / 100.0,
discountedSellingPrice = discountedSellingPrice / 100.0;
```

---

## 📊 Business Analysis & Insights

### ✅ Top 10 Best-Value Products
Identified products offering the highest discounts.

```sql
SELECT name, mrp, discountPercent
FROM zepto_v2
ORDER BY discountPercent DESC
LIMIT 10;
```

👉 Helps pricing teams highlight promotional products.

---

### ✅ High MRP but Out of Stock
Detected premium products currently unavailable.

**Business Risk:** Lost high-margin revenue.

---

### ✅ Estimated Revenue by Category
Calculated inventory revenue potential:

```sql
SELECT category,
SUM(discountedSellingPrice * availableQuantity) AS total_revenue
FROM zepto_v2
GROUP BY category;
```

👉 Enables category-level demand planning.

---

### ✅ Premium Products with Low Discount
Found products priced above ₹500 with minimal discounts.

**Insight:** Opportunity to improve conversions through targeted offers.

---

### ✅ Categories with Highest Average Discounts
Revealed aggressive pricing strategies across categories.

Useful for competitor benchmarking.

---

### ✅ Price Per Gram Analysis
Measured product value based on cost efficiency.

```sql
ROUND(discountedSellingPrice/weightInGms,2)
```

👉 Helps customers and pricing teams identify best-value products.

---

### ✅ Product Segmentation by Weight

Used CASE statements to classify products:

- Low (<1kg)  
- Medium (<5kg)  
- Bulk (>5kg)

Great for logistics and warehouse planning.

---

### ✅ Total Inventory Weight per Category
Estimated storage requirements and supply chain load.

---

## 💡 Key Business Insights

✔ Heavy discounts drive product attractiveness  
✔ Premium products going out-of-stock pose revenue risks  
✔ Inventory value varies significantly across categories  
✔ Price-per-gram is a strong indicator of product competitiveness  
✔ Bulk items require better warehouse planning  

---

## ⭐ Why This Project Stands Out

✅ Demonstrates strong SQL fundamentals  
✅ Shows business thinking — not just querying  
✅ Includes real data cleaning  
✅ Covers advanced aggregations  
✅ Portfolio-ready for Data Analyst roles  

---

## 📈 Real-World Applications

- Retail Analytics  
- Pricing Strategy  
- Inventory Optimization  
- Revenue Forecasting  
- Supply Chain Planning  

---

## 👨‍💻 Author

**Prince Kumar**  
Aspiring Data Analyst | SQL | Power BI | Business Analytics

---

## 🔥 Resume-Ready Bullet

**Performed end-to-end SQL data analysis on a quick-commerce inventory dataset, cleaning raw data and generating business insights on pricing, discounts, and revenue opportunities.**

---

⭐ If you found this project useful, consider starring the repository!

