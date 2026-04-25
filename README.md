# 📺 YouTube Data Analysis

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/priscilasalgadob/youtube-data-analysis/blob/main/Youtube_Data_Enhanced.ipynb)

A comprehensive exploratory data analysis (EDA) project using two large YouTube datasets: US comments (~691K rows) and trending video metadata across 10+ countries (~340K rows). The analysis covers sentiment, emoji behavior, engagement metrics by category, cross-variable correlations, and title formatting patterns.

---

## 🔍 Analysis Sections

### 1. 💬 Sentiment Analysis on Comments
- Loaded and cleaned ~691,000 US YouTube comments
- Applied **NLTK VADER** to compute compound polarity scores for every comment
- Segmented comments into **highly positive** (polarity ≥ 0.8) and **highly negative** (polarity ≤ −0.8) groups
  - 64,309 highly positive comments identified
  - 16,148 highly negative comments identified

### 2. ☁️ Word Cloud Visualization
- Generated word clouds for both positive and negative comment groups
- Applied standard stopword filtering to surface meaningful language patterns

### 3. 😂 Emoji Frequency Analysis
- Extracted all emojis from 691K comments using the `emoji` library
- Counted **288,886 total emojis** across the dataset
- Identified the **Top 10 most-used emojis**, led by 😂 (36,998), 😍 (33,453), and ❤️ (16,911)
- Visualized emoji distribution with an interactive Plotly bar chart

### 4. 📊 Trending Video Analysis (Multi-Country)
- Loaded and merged trending video CSVs from **10 countries**: US, UK, CA, MX, IN, DE, JP, KR, FR, RU
- Removed 36,417 duplicate rows, resulting in a clean dataset of **339,525 videos**
- Mapped numeric `category_id` to readable category names via YouTube's JSON category files
- Engineered engagement metrics:
  - `like_rate` = (likes / views) × 100
  - `dislike_rate` = (dislikes / views) × 100
  - `comment_rate` = (comment_count / views) × 100

### 5. 📈 Visualizations & Insights
| Chart | Description |
|-------|-------------|
| Box plot — Like Rate by Category | Median like rates across video categories, ordered by performance |
| Box plot — Dislike Rate by Category | Same breakdown for dislike rates |
| Regression plot — Views vs. Likes | Strong positive correlation (r ≈ 0.78) |
| Correlation Heatmap | views / likes / dislikes correlation matrix |
| Bar Chart — Top 20 Channels | Most frequently trending channels globally |
| Box plot — Punctuation in Titles vs. Views | Effect of punctuation count in video titles on view counts |

### 6. 🗄️ Data Export
- Saved a 1,000-row sample to CSV
- Loaded data into a **SQLite database** via SQLAlchemy for SQL-based querying

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas | Data loading, cleaning, merging, and feature engineering |
| NumPy | Numerical operations |
| NLTK (VADER) | Sentiment scoring on comment text |
| WordCloud | Visual representation of frequent words |
| Emoji | Emoji extraction and frequency counting |
| Matplotlib + Seaborn | Static charts (box plots, heatmap, regression plot) |
| Plotly | Interactive bar charts |
| SQLAlchemy | SQLite database export |
| Collections (Counter) | Emoji frequency counting |

---

## 📁 Project Structure

```
youtube-data-analysis/
│
├── Youtube_Data.ipynb              # Main analysis notebook
├── UScomments.csv                  # US YouTube comments dataset
├── additional_data/                # Trending video data per country
│   ├── USvideos.csv
│   ├── GBvideos.csv
│   ├── CAvideos.csv
│   ├── MXvideos.csv
│   ├── DEvideos.csv
│   ├── FRvideos.csv
│   ├── INvideos.csv
│   ├── JPvideos.csv
│   ├── KRvideos.csv
│   ├── RUvideos.csv
│   └── *_category_id.json          # Category mappings per country
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn nltk wordcloud emoji plotly sqlalchemy
```

Then download the VADER lexicon inside Python:

```python
import nltk
nltk.download('vader_lexicon')
```

### Running the Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/youtube-data-analysis.git
   cd youtube-data-analysis
   ```

2. Place your datasets in the correct directories (see Project Structure above).

3. Update any hardcoded file paths in the notebook to match your local directory.

4. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook Youtube_Data.ipynb
   ```

---

## 📌 Key Findings

- **😂 is the most-used emoji** across all US YouTube comments by a significant margin
- Positive comments outnumber highly negative ones by nearly **4:1** (64K vs. 16K)
- **Views and likes are strongly correlated** (r = 0.78), while dislikes show a weaker relationship
- **The Late Show with Stephen Colbert** had the most trending videos globally in the dataset, followed by WWE and Late Night with Seth Meyers
- This project is intended for educational and portfolio purposes

---

## 👤 Author

**Priscila Salgado**
- 📧 priscisb09@gmail.com
- 💼 [LinkedIn](https://www.linkedin.com/in/priscila-salgado-84914615b)
