# Amazon E-Commerce Sales Dashboard — Power BI




## Overview

An interactive **3-page Power BI dashboard** built on **128,975 Amazon India orders** (April – June 2022), spanning **9 product categories** across **69 states and union territories**. The dashboard transforms raw sales data into actionable insights on revenue trends, geographic performance, product mix, and order fulfilment.

---

## Dashboard Pages

| Page | Visuals Included |
|------|-----------------|
| **Sales Overview** | 4 KPI cards · Monthly revenue line chart · Order status donut chart · Date slicer |
| **Geographic Analysis** | State-wise revenue bubble map · Top states bar chart · State performance table · Category slicer |
| **Product & Orders** | Category revenue & units column chart · Fulfilment split pie chart · Size distribution 100% stacked bar · B2B slicer |

---

## Key Insights

- **Total Revenue:** ₹7.86 Cr (78,592,678 INR) across the full period
- **Total Orders:** 1,20,378 unique orders
- **Average Order Value:** ₹652.88 per order
- **Top revenue category:** Set (₹3.92 Cr) — nearly 2× higher than Kurta (₹2.13 Cr)
- **Peak month:** April 2022 at ₹2.88 Cr, followed by May and June
- **Top state:** Maharashtra led with ₹1.33 Cr, followed by Karnataka (₹1.05 Cr) and Telangana (₹0.69 Cr)
- **Cancellation rate:** 14.3% of all orders were cancelled — a significant operational concern
- **Fulfilment split:** 69.5% Amazon-fulfilled vs 30.5% Merchant-fulfilled
- **B2B share:** Only 0.7% of orders are B2B — this is overwhelmingly a B2C business

---

## DAX Measures Built

```dax
Total Revenue     = SUM('Amazon Sale Report'[Amount])
Total Orders      = DISTINCTCOUNT('Amazon Sale Report'[Order ID])
Total Units       = SUM('Amazon Sale Report'[Qty])
Avg Order Value   = DIVIDE([Total Revenue], [Total Orders])
Cancellation Rate = DIVIDE(
                      COUNTROWS(FILTER('Amazon Sale Report',
                        'Amazon Sale Report'[Status] = "Cancelled")),
                      [Total Orders]) * 100
```

---

## Tools & Techniques

| Area | Detail |
|------|--------|
| **Power Query** | Data cleaning, data type conversion, removed irrelevant columns (SKU, ASIN, promotion-ids, index) |
| **DAX** | 5 custom measures — Revenue, Orders, Units, Avg Order Value, Cancellation Rate |
| **Data Modelling** | Custom DateTable using `CALENDAR()`, relationship built to main dataset |
| **Visuals** | Card, Line chart, Donut, Bubble Map, Bar chart, Table, Clustered Column, Pie, 100% Stacked Bar, Slicers |
| **Theme** | Bloom (built-in Power BI theme) applied consistently across all 3 pages |

---

## Dataset

| Field | Detail |
|-------|--------|
| Source | Amazon India sales report |
| Period | April – June 2022 |
| Rows | 128,975 |
| Columns | 24 (18 used after cleaning) |
| File | `Amazon_Sale_Report.csv` |

**Key columns used:** Order ID, Date, Status, Category, Size, Amount, Qty, ship-city, ship-state, Fulfilment, B2B

---

## How to Open This Project

1. Download `Power_Bi_Dashboard.pbix`
2. Open with [Power BI Desktop](https://powerbi.microsoft.com/downloads/) — free to download
3. If the data doesn't load automatically, click **Transform Data → Data Source Settings** and update the path to point to `Amazon_Sale_Report.csv` on your machine

---

## Project Structure

```
amazon-sales-powerbi-dashboard/
├── Power_Bi_Dashboard.pbix     ← Main dashboard file
├── Amazon_Sale_Report.csv      ← Raw dataset (128,975 rows)
├── README.md                   ← This file
└── screenshots/
    ├── page1_sales_overview.png
    ├── page2_geographic.png
    └── page3_products.png
```

---

## Author

**Sumeet Rai**
[LinkedIn](https://linkedin.com/in/sumeetrai) · [GitHub](https://github.com/sumitrai3765-byte)

---

*Built as part of a data analytics portfolio. Tools used: Power BI Desktop, Power Query, DAX.*
