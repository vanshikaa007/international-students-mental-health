# international-students-mental-health
SQL analysis of how length of stay affects depression, social connectedness, and acculturative stress in international students.
# Analyzing International Students' Mental Health

## Overview
This project uses PostgreSQL to explore whether studying abroad affects 
international students' mental health, and whether length of stay is a 
contributing factor. Based on a 2019 study surveying students at a Japanese 
university, examining depression (PHQ-9), social connectedness (SCS), and 
acculturative stress (ASISS) scores.

## Tools Used
- PostgreSQL
- Datalab (SQL notebook environment)

## Dataset
`students.csv` — survey data including student type (international/domestic), 
language proficiency, academic level, age, length of stay, and mental health 
scores (PHQ-9, SCS, ASISS).

## Approach
Filtered the dataset to international students, grouped by length of stay 
(in years), and calculated average depression, social connectedness, and 
acculturative stress scores per group.

```sql
SELECT stay,
    COUNT(inter_dom) AS count_int,
    ROUND(AVG(todep),2) AS average_phq,
    ROUND(AVG(tosc),2) AS average_scs,
    ROUND(AVG(toas),2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
