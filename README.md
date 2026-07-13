# Healthcare-PowerBI-Dashboard

# 📌 Project Overview

This project demonstrates the development of an **interactive Healthcare Analytics Dashboard** using **Microsoft Power BI**.

The dashboard transforms raw healthcare records into meaningful business insights that help hospitals monitor:

- Patient Admissions
- Bed Utilization
- Doctor Performance
- Billing & Insurance
- Disease Trends
- Operational KPIs

The dashboard was designed following a real-world Business Intelligence workflow including data cleaning, data modeling, DAX calculations, dashboard design, and visualization best practices.

---

# 🎯 Business Problem

Hospitals generate thousands of patient records every day.

Hospital management wants to answer questions such as:

- How many patients were admitted?
- Which diseases are most common?
- Which bed types are highly occupied?
- How much revenue was generated?
- How much amount is covered by insurance?
- Which doctors receive better patient feedback?
- Which patients require follow-up?

Instead of manually analyzing spreadsheets, management needs an interactive dashboard.

---

# 🗂 Dataset

The dataset contains approximately **7,000+ patient records**.

| Column | Description |
|---------|-------------|
| Patient ID | Unique patient identifier |
| Admit Date | Date of hospital admission |
| Discharge Date | Date of discharge |
| Diagnosis | Disease diagnosed |
| Bed Occupancy | ICU / General / Private |
| Test | Medical test performed |
| Doctor | Assigned doctor |
| Follow-up Date | Scheduled follow-up |
| Feedback | Rating (Out of 5) |
| Billing Amount | Hospital charges |
| Health Insurance Amount | Insurance covered amount |

---

# 🛠 Technology Stack

- Power BI Desktop
- Power Query
- DAX
- Excel / CSV
- Data Modeling
- Interactive Visualizations

---

# 📊 Dashboard Layout

```
---------------------------------------------------------------
 Logo              Patient ID              Date Range Filter
---------------------------------------------------------------

 Admit Date | Discharge Date | Follow-up | Billing Amount

---------------------------------------------------------------

 Bed Occupancy     Doctor Feedback      Diagnosis Distribution

---------------------------------------------------------------

 Billing Amount vs Insurance Amount

---------------------------------------------------------------
```

---

# 🔄 Project Workflow

## Step 1 : Data Import

Imported the healthcare dataset into Power BI.

Source:

- Excel
- CSV

---

## Step 2 : Power Query

Performed data cleaning.

### Transformations

✔ Changed Data Types

✔ Renamed Columns

✔ Removed Errors

✔ Converted Dates

✔ Checked Null Values

✔ Validated Numeric Columns

---

## Step 3 : Data Modeling

No complex relationships were required because the project uses a single fact table.

Power BI automatically creates relationships if additional lookup tables are introduced.

---

# 📊 Dashboard Visualizations

---

# 1️⃣ Patient ID Slicer

## Purpose

Allows users to select any patient.

After selecting a Patient ID, every visual updates automatically.

### Business Use

Hospital staff can instantly retrieve:

- Admit Date
- Discharge Date
- Billing
- Diagnosis
- Doctor
- Follow-up

instead of searching manually.

---

# 2️⃣ Date Range Slicer

## Purpose

Filters the dashboard by Admit Date.

Users can analyze:

- Monthly data
- Quarterly data
- Yearly data

### Example

January 2024

↓

Only patients admitted during January 2024 are displayed.

---

# 3️⃣ Admit Date Card

## Visualization

Card

### Shows

Admission date of selected patient.

### Business Value

Quick patient lookup.

---

# 4️⃣ Discharge Date Card

## Visualization

Card

### Shows

Patient discharge date.

### Business Value

Useful for

- Length of stay
- Hospital planning

---

# 5️⃣ Follow-up Date Card

## Visualization

Card

### Shows

Next follow-up appointment.

### Business Value

Improves patient management.

---

# 6️⃣ Billing Amount Card

## Visualization

Card

### Shows

Total billing amount for selected patient.

### Business Value

Quick financial overview.

---

# 7️⃣ Bed Occupancy Chart

## Visualization

Clustered Column Chart

### Axis

X-Axis

- Bed Type

Y-Axis

- Number of Patients

### Categories

- ICU
- General
- Private

### Business Question

Which bed type is utilized the most?

### Insight

Helps hospital administration plan infrastructure expansion.

---

# 8️⃣ Doctor Feedback Chart

## Visualization

Donut Chart

### Measure

Average Feedback

or

Count of Ratings

### Business Question

Which doctors receive higher patient satisfaction?

### Insight

Useful for

- Performance evaluation
- Training
- Recognition

---

# 9️⃣ Diagnosis Distribution

## Visualization

Funnel Chart

### Categories

Examples

- Viral Infection
- Malaria
- Pneumonia
- Typhoid

### Business Question

Which diseases occur most frequently?

### Insight

Helps understand disease trends.

---

# 🔟 Billing vs Insurance

## Visualization

Line Chart

### X-Axis

Admit Date

### Y-Axis

- Billing Amount
- Insurance Amount

### Business Question

How much of the patient's bill is covered by insurance?

### Insight

Identifies

- Insurance gap
- Revenue trends

---

# 🎨 Dashboard Design

Design principles followed

✔ Healthcare Theme

✔ Consistent Colors

✔ White Background

✔ Blue Accent

✔ Interactive Filters

✔ Minimal Layout

✔ Professional Typography

---

# 📐 DAX Measures

Below are recommended DAX measures used (or that can be used) to power the dashboard.

---

## Total Patients

```DAX
Total Patients =
DISTINCTCOUNT('Healthcare'[Patient ID])
```

Purpose

Returns total unique patients.

---

## Total Billing

```DAX
Total Billing =
SUM('Healthcare'[Billing Amount])
```

Purpose

Calculates total hospital revenue.

---

## Total Insurance Amount

```DAX
Total Insurance =
SUM('Healthcare'[Health Insurance Amount])
```

Purpose

Calculates total insurance coverage.

---

## Insurance Gap

```DAX
Insurance Gap =
SUM('Healthcare'[Billing Amount])
-
SUM('Healthcare'[Health Insurance Amount])
```

Purpose

Shows amount paid by patients.

---

## Average Feedback

```DAX
Average Feedback =
AVERAGE('Healthcare'[Feedback])
```

Purpose

Measures overall doctor performance.

---

## Total Admissions

```DAX
Admissions =
COUNTROWS('Healthcare')
```

Purpose

Counts hospital admissions.

---

## Average Billing

```DAX
Average Billing =
AVERAGE('Healthcare'[Billing Amount])
```

Purpose

Average patient bill.

---

## Total ICU Patients

```DAX
ICU Patients =
CALCULATE(
COUNTROWS('Healthcare'),
'Healthcare'[Bed Occupancy]="ICU"
)
```

Purpose

Returns ICU occupancy.

---

## Private Bed Count

```DAX
Private Beds =
CALCULATE(
COUNTROWS('Healthcare'),
'Healthcare'[Bed Occupancy]="Private"
)
```

---

## General Bed Count

```DAX
General Beds =
CALCULATE(
COUNTROWS('Healthcare'),
'Healthcare'[Bed Occupancy]="General"
)
```

---

## Average Hospital Stay

```DAX
Average Stay =
AVERAGEX(
Healthcare,
DATEDIFF(
Healthcare[Admit Date],
Healthcare[Discharge Date],
DAY
)
)
```

Purpose

Calculates average patient stay.

---

## Patients Requiring Follow-up

```DAX
Follow Up Patients =
COUNTROWS(
FILTER(
Healthcare,
NOT(ISBLANK(Healthcare[Follow-up Date]))
)
)
```

---

## Monthly Revenue

```DAX
Monthly Revenue =
SUM(Healthcare[Billing Amount])
```

(Used with Month on X-axis.)

---

# 📈 KPIs

Dashboard tracks

- Total Patients
- Total Revenue
- Insurance Coverage
- Average Feedback
- Bed Occupancy
- Disease Distribution
- Follow-up Patients

---

# 📌 Business Insights Generated

The dashboard enables management to:

✔ Monitor hospital occupancy

✔ Compare revenue with insurance coverage

✔ Track disease trends

✔ Measure doctor performance

✔ Monitor patient follow-ups

✔ Improve operational efficiency

---

# 🚀 Future Improvements

- SQL Database Integration
- Real-time Streaming Dashboard
- Role-Level Security (RLS)
- Drill-through Pages
- Forecasting using Power BI AI
- Patient Readmission Prediction
- Doctor Performance Scorecards
- Automated Email Reports
- Mobile Dashboard Optimization
