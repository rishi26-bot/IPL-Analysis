# 🏏 IPL Data Analysis: Player Performance, Toss Impact & Venue Trends

An end-to-end exploratory data analysis of the Indian Premier League (2008-2024) using Python. The project answers practical, strategy-oriented questions that a team analyst or broadcaster might ask, and turns ball-by-ball data into charts and insights.

**Tech stack:** Python · pandas · matplotlib · seaborn · SciPy

---

## 📌 Business Questions

1. **Toss impact:** Does winning the toss actually help win the match? Is "field first" really the better choice?
2. **Venue trends:** Which grounds are high-scoring? Which favour chasing teams?
3. **Player performance:** Who are the top batters and bowlers once strike rate, average and economy are considered, not just raw totals?
4. **Match phases:** How does scoring change across powerplay, middle and death overs?

## 📂 Dataset

[IPL Complete Dataset (2008-2024) on Kaggle](https://www.kaggle.com/datasets/patrickb1912/ipl-complete-dataset-20082020)

| File | Description |
|------|-------------|
| `matches.csv` | One row per match: season, venue, teams, toss, winner, player of the match |
| `deliveries.csv` | One row per ball: batter, bowler, runs, extras, wickets |

Download both files into the `data/` folder (see `data/README.md`).

## 🗂️ Project Structure

```
ipl-analysis/
├── data/               # matches.csv, deliveries.csv (not committed)
├── images/             # generated charts
├── outputs/            # generated tables + key_findings.md
├── src/
│   └── analysis.py     # full analysis pipeline
├── requirements.txt
└── README.md
```

## 🚀 How to Run

```bash
git clone https://github.com/<your-username>/ipl-analysis.git
cd ipl-analysis
pip install -r requirements.txt

# add matches.csv and deliveries.csv to data/
python src/analysis.py
```

Charts are saved to `images/`, tables to `outputs/`, and a summary of insights to `outputs/key_findings.md`.

## 🧹 Data Cleaning & Methodology

- **Team names standardised**, e.g. Delhi Daredevils → Delhi Capitals, Kings XI Punjab → Punjab Kings.
- **Venue names normalised** (city suffixes removed, renamed stadiums merged, e.g. Feroz Shah Kotla → Arun Jaitley Stadium).
- **Season labels fixed** (the dataset uses labels such as `2007/08` and `2020/21`).
- **No-result matches excluded** from win-based analysis.
- **Super overs excluded** from all ball-by-ball stats.
- **Cricket-correct metrics:**
  - Balls faced exclude wides; bowler legal balls exclude wides and no-balls.
  - Byes and leg-byes are not charged to the bowler.
  - Run outs and retirements are not counted as bowler wickets.
  - Leaderboards use minimum-ball thresholds to avoid small-sample noise.
- **Statistical test:** a binomial test checks whether the toss winner's win rate differs from 50%, rather than just eyeballing percentages.

## 📊 Results

> Run the script, then copy the numbers from `outputs/key_findings.md` into this section.

### 1. Toss Impact
![Toss impact](images/02_toss_impact.png)

**Finding:** _<e.g. Toss winners won X% of matches (p = …). Chasing is chosen in Y% of tosses.>_

### 2. Venue Trends
![Venue trends](images/03_venue_trends.png)

**Finding:** _<highest-scoring venue, most chase-friendly venue>_

### 3. Batting
![Batting](images/04_batting.png)

**Finding:** _<top run scorer, best strike rate with 1000+ runs>_

### 4. Bowling
![Bowling](images/05_bowling.png)

**Finding:** _<top wicket taker, most economical bowler>_

### 5. Run Rate by Over
![Run rate by over](images/06_run_rate_by_over.png)

**Finding:** _<powerplay vs middle vs death-over scoring rates>_

## 💡 Recommendations

_Fill in after reviewing your results. Examples of the kind of conclusions to draw:_

- Toss strategy: whether captains should prefer fielding first, and whether that holds at every venue.
- Squad building: which venues need big-hitting batters vs. defensive bowlers.
- Auction value: players who combine high strike rate with a strong average.

## ⚠️ Limitations

- Ball-by-ball data does not capture pitch conditions, dew, weather or player form.
- Toss and venue effects can overlap; a deeper analysis could control for team strength.
- Franchise changes (e.g. Deccan Chargers vs Sunrisers Hyderabad) are treated as separate teams.

## 🔭 Future Work

- Build an interactive dashboard in Power BI / Tableau / Streamlit.
- Predict match winners with logistic regression using toss, venue and team features.
- Add bowler-vs-batter matchup analysis and phase-wise player ratings.

## 🙋 Author

(https://www.linkedin.com/in/rushikesh-uke-921081290/) · 
