# 🎵 Maryam Music

> Exploratory data analysis and feature engineering to understand and predict customer churn for a music streaming service.

---

## 📌 Background

Maryam Music is a streaming service (est. 1996) that has been experiencing higher-than-usual customer cancellations over the past few months. This project takes on the role of a Jr. Data Scientist tasked with using data science to investigate the issue and lay the groundwork for a predictive churn model.

---

## 🎯 Objectives

1. **Scope** the data science project
2. **Gather** the data in Python
3. **Clean** the data
4. **Explore & visualize** the data
5. **Prepare** the data for modeling

---

## 📂 Repository Structure

```
maryam-music-churn/
│
├── mm_notebook.ipynb                    # Main analysis notebook
├── maryam_music_customers.csv           # Customer subscription data
├── maryam_music_listening_history.xlsx  # Listening history (3 sheets)
│   ├── Sheet 1: Listening History       # Per-session audio play logs
│   ├── Sheet 2: Audio                   # Song/podcast metadata with genre & popularity
│   └── Sheet 3: Sessions                # Session login timestamps
└── README.md
```

---

## 🗂️ Data Overview

### `maryam_music_customers.csv`
| Column | Description |
|---|---|
| Customer ID | Unique customer identifier |
| Customer Name | Full name |
| Email | Contact email |
| Member Since | Subscription start date |
| Subscription Plan | Plan tier (e.g., Basic with Ads) |
| Subscription Rate | Monthly rate |
| Discount? | Whether a discount was applied |
| Cancellation Date | Date of cancellation (NaN = active) |

### `maryam_music_listening_history.xlsx`
- **Listening History**: tracks each audio item played per session per customer
- **Audio**: metadata for songs and podcasts including genre and popularity score
- **Sessions**: login timestamps for each session ID

---

## 🔧 Methodology

### 1. Data Gathering
- Loaded customer data from CSV and listening history from a multi-sheet Excel file using `pandas`

### 2. Data Cleaning
- Audited and converted data types (dates, currency strings → numeric)
- Standardized inconsistent genre labels (e.g., `"Pop"` vs `"Pop Music"`)
- Cleaned malformatted email fields
- Handled missing values in `Subscription Plan`, `Discount?`, and `Cancellation Date`
- Removed duplicate records

### 3. Exploratory Data Analysis
- Visualized churn distribution across subscription plans and discount status
- Analyzed listening session frequency between churned and active customers
- Explored genre preference patterns (Pop, Podcasts, etc.) by churn status
- Generated correlation heatmaps and pairplots

### 4. Feature Engineering (Model Prep)
The final modeling dataframe (`model_df`) includes:

| Feature | Description |
|---|---|
| `Customer ID` | Unique identifier |
| `Cancelled` | **Target variable** — 1 if cancelled, 0 if active |
| `Discount?` | Binary discount flag |
| `Number of Sessions` | Total listening sessions in the period |
| `Pop Percentage` | Share of listening time spent on Pop music |
| `Podcasts Percentage` | Share of listening time spent on Podcasts |

---

## 🛠️ Tech Stack

- **Python 3.13**
- `pandas` — data loading, cleaning, and transformation
- `numpy` — numerical operations
- `seaborn` — data visualization

---

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/your-username/maryam-music-churn.git
cd maryam-music-churn

# Install dependencies
pip install pandas numpy seaborn openpyxl jupyter

# Launch the notebook
jupyter notebook mm_notebook.ipynb
```

---

## 🔮 Possible Next Steps

- Train a supervised classification model (e.g., Logistic Regression, Random Forest) on `model_df` to predict churn
- Evaluate model performance with cross-validation
- Identify high-risk customers for targeted retention campaigns
