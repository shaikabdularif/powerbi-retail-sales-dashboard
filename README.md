# Commercial Sales & Profitability Dashboard (Power BI)

An executive-level Business Intelligence solution built in Power BI to monitor commercial sales performance, gross profit margins, and predictive run rates across regional distribution channels.

## Dashboard Highlights
- **Executive KPI Cards:** Real-time visibility into Total Net Sales, Gross Margin %, Average Order Value (AOV), and Quantity Sold.
- **Dimensional Breakdown:** Interactive slicing by Region/Market, Product Category, and Sales Channel (Retail vs. Online).
- **Time-Series Analysis & Forecasting:** Historical sales trends integrated with 30-day forward demand projections.
- **Relational Data Model:** Structured Star Schema isolating transactional sales facts from Customer, Product, Region, and Calendar dimension tables.

## Key DAX Formulas Used
```dax
Total Net Sales = SUM(Fact_Sales[Sales_Amount])

Total Cost = SUM(Fact_Sales[Cost_Amount])

Gross Margin = [Total Net Sales] - [Total Cost]

Gross Margin % = DIVIDE([Gross Margin], [Total Net Sales], 0)

YoY Sales Growth = 
VAR PrevYear = CALCULATE([Total Net Sales], SAMEPERIODLASTYEAR(Dim_Date[Date]))
RETURN DIVIDE([Total Net Sales] - PrevYear, PrevYear, 0)
