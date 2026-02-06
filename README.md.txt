# ⚽ AFCON 2025 Tournament Analytics Dashboard
## Power BI End-to-End Data Analytics Project

![AFCON 2025 Dashboard](screenshots/dashboard_overview.png)

---

## 🌍 Project Summary

This project delivers a **complete end-to-end sports analytics solution** built in Power BI, focused on the AFCON 2025 tournament hosted in Morocco (December 21, 2025 - January 18, 2026).

**The goal was simple:** Transform raw tournament data into a compelling, interactive dashboard that answers real analytical questions around:
- Tournament performance metrics
- Team discipline and playing style
- Stadium attendance patterns
- Referee impact analysis
- Team attacking efficiency

This repository showcases my ability to move from **raw data → data modeling → DAX → interactive storytelling**, demonstrating the full analytics workflow expected from a professional Power BI / Data Analyst.

---

## 🖥️ Dashboard Snapshot

The dashboard provides an **executive-style overview** of the tournament, highlighting the most important KPIs at a glance while allowing deeper interactive exploration.

### Key Headline Metrics:
- **52 Matches Played** across 9 stadiums
- **121 Goals Scored** (2.33 average per match)
- **1.3M Total Tournament Attendance**
- **218 Total Cards Issued** (210 yellow, 8 red)

### Interactive Features:
- **Team Filter:** Drill down into any team's performance
- **Group Filter:** Analyze group stage vs knockout dynamics
- **Stage Filter:** Compare performance across tournament phases
- **Multi-dimensional Analysis:** Shots vs Goals effectiveness, Discipline by Team, Referee Performance, Stadium Analytics

---

## 🎯 Why This Project Matters

Sports analytics is a **perfect real-world data scenario** that mirrors business analytics challenges:
- **Multiple entities** (teams, referees, stadiums, matches) requiring relational modeling
- **Aggregation challenges** (attendance, cards, goals) demanding careful DAX measures
- **Need for clean modeling** to prevent double-counting and ensure accuracy
- **Storytelling requirements** to communicate insights to non-technical stakeholders

This project demonstrates the full analytics workflow from data preparation to dashboard delivery, showcasing skills directly transferable to business intelligence roles.

---

## 🛠 Tools & Technologies

| Tool | Role in Project |
|------|----------------|
| **Power BI Desktop** | Dashboard development & data modeling |
| **Power Query** | Data preparation & transformation |
| **DAX** | KPI calculations & analytical measures |
| **Microsoft Word** | Comprehensive technical report (20+ pages) |
| **GitHub** | Project documentation & version control |
| **Data Sources** | FotMob, Opta Sports, CAF Official Records |
| **Microsoft Excel** | Dataset design & construction from scratch

---

## 🧹 Data Preparation & Transformation

The dataset was **designed and modeled from scratch**, then prepared for analytics using Power Query.

### Key Preparation Steps:
✅ **Data Structuring** - Consolidated tournament data into a single analytical dataset  
✅ **Standardization** - Unified team and referee naming conventions across sources  
✅ **Data Quality** - Resolved duplicate entries and inconsistencies    
✅ **Derived Columns** - Created match-level metrics (cards per match, goals per match)  
✅ **Validation** - Cross-checked totals against official tournament summaries

These steps ensured the dataset behaved like a **real-world analytics dataset** with proper granularity and reliability.

---




## 🧩 Data Modeling Approach

A **structured Power BI data model** was built to support reliable and scalable analysis.

### Key Modeling Decisions:
- **Match-centric design:** Match_ID as the primary grain for all calculations
- **Optimized filtering:** Proper filter context propagation across visuals
- **Aggregation safety:** Prevention of double-counting in attendance and card metrics
- **Measure-based reporting:** All KPIs calculated via DAX measures (not calculated columns)
- **Relationship integrity:** Proper handling of many-to-one relationships

---

## 📐 Key DAX Measures

### Matches Played
```DAX
Matches Played = DISTINCTCOUNT(Sheet1[Match_ID])
```
*Counts unique matches to establish tournament scope*

### Total Goals
```DAX
Total Goals = SUM(Sheet1[Total_Goals])
```
*Aggregates goals scored across all matches*

### Average Goals per Match
```DAX
Avg Goals per Match = 
DIVIDE([Total Goals], [Matches Played])
```
*Calculates tournament-wide scoring rate with zero-error handling*

### 🎟️ Total Attendance (Critical Measure)

**Challenge:** Attendance values were duplicated in the source data (one row per team per match), creating double-counting issues.

**Solution:** Custom measure using SUMX and VALUES to ensure each match's attendance is counted only once.

```DAX
Total Attendance =
SUMX(
    VALUES(Sheet1[Match_ID]),
    CALCULATE(
        AVERAGE(Sheet1[Match_Attendance])
    )
)
```
*Prevents double-counting of attendance per fixture - a common real-world reporting issue*

### Total Cards
```DAX
Total Cards = 
SUM(Sheet1[YellowCards]) + SUM(Sheet1[RedCards])
```
*Combines yellow and red card discipline tracking*

---

## 📊 Insights Delivered

### ⚽ Tournament Overview
The competition delivered a **balanced attacking tournament** with over 2 goals per match on average (2.33), indicating offensive quality across the 24-team field.

### 🎯 Team Effectiveness Analysis
The **Shots vs Goals scatter plot** reveals the relationship between attacking volume and scoring efficiency:
- **Nigeria** led in total goals (14) with strong shot accuracy (45.6%)
- **Senegal** (champions) demonstrated best shot accuracy (50.0%) with 108 total shots
- **High-efficiency outliers** like Ivory Coast converted 50% of shots on target
- **Volume shooters** like Morocco and Egypt took 108 and 72 shots respectively

**Key Insight:** Shooting accuracy matters more than shot volume for tournament success.

### 🟨 Discipline Trends
Card distribution varies significantly between teams, revealing playing style and tactical approaches:
- **Mali:** Tournament's most disciplined issues (19 total cards: 16 yellow, 3 red)
- **Nigeria & Senegal:** High physicality (17 cards each) but zero red cards for Nigeria and 1 for Senegal showed controlled aggression
- **DR Congo:** Exceptional discipline (only 3 cards despite reaching Round of 16)

**Finding:** Teams with 3+ red cards (Mali, Equatorial Guinea, Uganda) all eliminated before or in the quarterfinals for Mali.

### 👨‍⚖️ Referee Performance Analysis
Referee card averages highlight officiating differences across the tournament:
- **Waweru Peter (Kenya):** 7.0 cards per match (highest) - officiated high-pressure knockout fixtures
- **Ahmad Heeralall (Mauritius):** 1.0 cards per match (lowest) - group stage matches
- **Regional representation:** 29 referees from 22 African nations ensured continental balance

**Insight:** Card issuance correlates with match pressure level, not referee bias.

### 🏟️ Stadium Attendance Analytics
Attendance trends reveal clear variation across venues:
- **Stade Prince Moulay Abdallah (Rabat):** 91.8% fill rate across 7 matches (tournament's most efficient venue)
- **Attendance range:** 4,013 (South Africa vs Sudan) to 66,526 (Final) = 16.6x variance
- **Key driver:** Match significance and host nation involvement > venue infrastructure quality

**Recommendation:** Dynamic venue-to-fixture matching using predictive modeling for future tournaments.

---

## 📁 Repository Structure

```
AFCON-2025-Analytics/
│
├── dashboard/
│   └── AFCON_2025_PROJECT.pbix        # Interactive Power BI dashboard
│
├── reports/
│   └── AFCON_2025_Technical_Report.docx   # 50+ page comprehensive analysis
│
├── screenshots/
│   └── dashboard_overview.png         # Dashboard preview image
│
└── README.md                          # Project summary


## 🚀 How to View the Dashboard

1. **Download** the `.pbix` file from the `dashboard/` folder
2. **Install** Power BI Desktop (free) from [Microsoft's website](https://powerbi.microsoft.com/desktop/)
3. **Open** the file in Power BI Desktop
4. **Explore** using interactive filters and slicers:
   - Select specific teams to see their stats
   - Filter by tournament stage (Group, R16, QF, SF, Final)
   - Drill into referee performance metrics
   - Analyze stadium attendance patterns

---

## 📄 Technical Report

The **20+ page comprehensive report** (available in `reports/` folder) includes:

### Section Breakdown:
1. **Tournament Overview** - Match statistics, key moments, final standings
2. **Team Effectiveness Analysis** - All 24 teams' offensive/defensive metrics
3. **Player Impact Analysis** - Top performers, goals + assists rankings, contextual evaluation
4. **Referee Performance** - 29 officials from 22 nations, cards per match variance
5. **Stadium & City Analytics** - 9 venues across 8 Moroccan cities, attendance optimization
6. **Institutional Analysis** - Referee development budgets, partnership gaps (Nigeria case study)
7. **Strategic Recommendations** - Team-specific improvements, federation priorities, CAF enhancements
8. **Data Methodology** - Sources, validation protocols, analytical approach

### Key Report Findings:

**📊 Statistical Excellence ≠ Tournament Success**
- Ademola Lookman: 7 G+A (tournament high) → Bronze Medal
- Brahim Díaz: 5 goals (Golden Boot) → Silver Medal
- Pape Gueye: 3 goals (final winner) → **CHAMPION**

*Insight: One extra-time final goal outweighed entire tournament's statistical dominance*

** Nigeria's Performance**
- Tournament-leading 14 goals from 8 different scorers (adequate depth)
- Failed to score in both decisive knockout matches (0-0 vs Morocco in SF, 0-0 vs Egypt in bronze final)
- ** Recommendation:** Mental strength gap under maximum pressure, not talent deficiency

**⚖️ Referee Development Disparity**
- Morocco: $8.2M investment (12.6% of budget) → 2 AFCON referees
- Egypt: $1.8M investment (12.5% of budget) → 2 AFCON referees  
- Nigeria: $131K investment (1.45% of budget) → 0 AFCON referees

*Finding: Nations investing $500K+ annually consistently place 3+ officials at continental tournaments*

---

## 💡 Skills Demonstrated

### Technical Skills:
✅ **Data Cleaning & Transformation** - Power Query ETL workflows  
✅ **Data Modeling** - Relational model design, grain definition, relationship management  
✅ **DAX & Analytical Calculations** - Measures, filter context manipulation  
✅ **Interactive Dashboard Design** - UX/UI principles, visual hierarchy, filter optimization  
✅ **Data Storytelling** - Translating complex data into actionable business insights

### Analytical Skills:
✅ **Exploratory Data Analysis** - 24-team statistical profiling  
✅ **Correlation Analysis** - Budget-to-performance relationships  
✅ **Comparative Analysis** - Cross-team, cross-venue, cross-referee benchmarking  
✅ **Root Cause Analysis** - Nigeria's referee crisis institutional evaluation

### Business Skills:
✅ **Requirements Gathering** - Defining analytical questions stakeholders need answered  
✅ **Stakeholder Communication** - Writing technical reports for diverse audiences  
✅ **Strategic Recommendations** - Converting insights into actionable next steps  
✅ **Project Documentation** - GitHub repository management, version control

---

## 🎓 Learning Outcomes

This project reinforced critical data analytics principles:

1. **Data quality matters more than data volume** - Spent 40% of project time on cleaning/validation
2. **Measure design prevents errors** - Careful DAX eliminated double-counting issues
3. **Context drives insight** - Raw statistics mislead without understanding match situations
4. **Documentation enables impact** - Comprehensive reporting ensures findings are actionable

---

## 📬 Connect With Me

**[Your Name]** Lamini Katu Abel  
📧 sarkinkolo539@gmail.com  
💼 [LinkedIn Profile URL] https://www.linkedin.com/in/lamini-abel-b7958b122/  


## ⭐ Feedback & Contributions

**Found this project interesting?**
- ⭐ Star this repository to show your support
- 💬 Open an issue if you spot data discrepancies or have suggestions
- 🤝 Connect with me on LinkedIn to discuss sports analytics

---

## 📝 Data Attribution & Methodology

### Primary Sources:
- **FotMob:** Match statistics, player performance metrics
- **Opta Sports:** Advanced analytics
- **CAF:** Official tournament records, referee assignments, attendance figures

### Validation Protocol:
- Cross-source verification (FotMob vs Opta variance <2%)
- Official CAF records used as final authority for discrepancies
- Manual validation of attendance figures against match reports

### Limitations:
- Budget data for some federations estimated from FIFA Forward reports
- Qualitative factors (team morale, leadership) captured narratively, not quantitatively

*Data accurate as of January 18, 2026 (AFCON 2025 Final)*

**Built with 📊 passion by Lamini Katu Abel | Sports Data Analytics Portfolio Project**

*Demonstrating end-to-end analytics capabilities: Data Collection → Modeling → Visualization → Insights*

