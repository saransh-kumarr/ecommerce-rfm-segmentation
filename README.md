# 🛒 Olist Customer Intelligence — RFM Segmentation & Revenue Analysis

> Analyzed 100,000+ real Brazilian e-commerce orders to identify customer segments, revenue patterns, and retention problems.

---

## 📌 Problem Statement

Who are our customers, and where is revenue really coming from?

Olist has 100k+ orders but no visibility into customer behavior. This project answers:
- Which customers are high-value vs at-risk?
- What does retention actually look like?
- Where is revenue concentrated, and when does it drop?

---

## 📁 Dataset

**OLIST Brazilian E-commerce** — [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

- 100k+ real orders (2016–2018)
- 9 tables: customers, orders, payments, order_items, products, sellers, reviews, geolocation, category translations
- Multi-table, messy, real-world

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python + Pandas | Cleaning, merging, analysis |
| scikit-learn (KMeans, StandardScaler) | Customer segmentation |
| Matplotlib / Seaborn | EDA + cohort heatmap |
| Power BI Desktop | Final dashboard |
| Jupyter Notebook | Development |

---

## 📂 Project Structure

```
olist-customer-intelligence/
│
├── dashboard/
│   └── olist_dashboard.pbix
├── data/
│   └── (not uploaded — download from Kaggle link above)
├── images/
│   ├── aov_trend.png
│   ├── cohort_heatmap.png
│   ├── elbow_plot.png
│   ├── kmeans_clusters.png
│   ├── monthly_revenue.png
│   ├── segment_distribution.png
│   └── top_categories.png
├── notebooks/
│   ├── 01_exploration.ipynb
│   ├── 02_cleaning.ipynb
│   ├── 03_rfm_analysis.ipynb
│   ├── 04_kmeans_clustering.ipynb
│   ├── 05_revenue_analysis.ipynb
│   └── 06_cohort_analysis.ipynb
├── .gitignore
├── LICENSE
└── README.md
```

---

## 🔍 What I Did

### 1. Data Engineering
- Loaded and explored all 9 CSVs
- Cleaned nulls, duplicates, fixed dtypes (string → datetime)
- Merged 5 tables into one `cleaned_master.csv`

### 2. RFM Analysis
- Calculated **Recency** (days since last order), **Frequency** (total orders), **Monetary** (total spend) per customer
- Scored each metric 1–5 using quantile binning
- Output: `rfm_scores` dataframe with segment labels

### 3. KMeans Clustering
- Normalized RFM with StandardScaler
- Used Elbow method to select k=4
- Labeled 4 segments: **Recent**, **Lost**, **Loyal**, **High Value**

### 4. Revenue Analysis
- Monthly revenue trend (2016–2018)
- Top product categories by revenue
- Average Order Value over time

### 5. Cohort Retention Analysis
- Grouped customers by first purchase month
- Tracked return rate each subsequent month
- Built retention heatmap

---

## 📊 Key Findings

- **22,228 at-risk customers** identified — largest segment, need re-engagement campaigns
- **<1% Month-1 retention** vs 20–30% industry average — critical retention problem
- **bed_bath_table + health_beauty** = top 2 categories, **3.28M BRL** combined revenue
- **Revenue peaked May, sharp drop from September** — clear seasonality pattern
- **Total Revenue: 19.77M BRL | AOV: 171.91 BRL | Total Orders: 96.47K**

---

## 📈 Dashboard

4-page Power BI dashboard:

| Page | Content |
|------|---------|
| Revenue Overview | Monthly trend, total revenue, AOV |
| Customer Segments | RFM clusters, segment sizes, revenue per segment |
| Cohort Retention | Retention heatmap by cohort month |
| Business Recommendations | Insights + supporting visuals |

*(Add dashboard screenshot here)*

---

## ▶️ How to Run

```bash
# 1. Clone repo
git clone https://github.com/yourusername/olist-customer-intelligence.git
cd olist-customer-intelligence

# 2. Install dependencies
pip install -r requirements.txt

# 3. Download dataset from Kaggle and place CSVs in /data

# 4. Run notebooks in order (01 → 06)
jupyter notebook
```

**requirements includes:** pandas, numpy, scikit-learn, matplotlib, seaborn, jupyter

---

## 💡 Business Recommendations

1. **Re-engage at-risk segment (22K customers)** — email campaign with discount, targeting customers with high past spend but no recent orders
2. **Fix Month-1 retention** — post-purchase follow-up sequence within 30 days; current <1% is the biggest revenue leak
3. **Double down on bed_bath_table + health_beauty** — top revenue categories; inventory and marketing priority
4. **Prepare for September seasonality drop** — run promotions in August to smooth the revenue dip

---
