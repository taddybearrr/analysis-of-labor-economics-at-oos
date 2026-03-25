# Analysis on On One Studios' Labor Economics

## Overview

This repository documents a data analysis project for **On One Studios (OOS)** focused on connecting **Mindbody (MB)** operational data with **QuickBooks Online (QBO)** financial data to better understand class and program economics.

The goal of this project is to help stakeholders evaluate the studio's labor economics, financial sustainability, and operational efficiency through a structured analytics workflow.

## Business Context

On One Studios currently has a disconnect between:

* **Mindbody**, which shows operational activity such as attendance, visits, classes, memberships, and sales behavior
* **QuickBooks Online**, which reflects financial outcomes such as payroll, overhead, and accounting structure

This project aims to bridge those systems so OOS can make better decisions around:

* class viability
* mentor compensation
* schedule planning
* program performance
* overall path to profitability

## Stakeholders

* **Tad Racca** — Data Analyst
* **Kevin Nguyen** — Primary stakeholder, On One Studios
* Additional presentation audience may include:

  * Donita Battad (Co-Owner)
  * Kevin Breis (Co-Owner)
  * Joanne Pearl (Studio Coordinator)

## Problem Statement

OOS needs a clearer way to connect operational behavior to financial outcomes.

Right now, the studio can observe attendance, visits, memberships, and sales activity in Mindbody, while QuickBooks contains the financial reality of payroll, overhead, and related business costs. However, without a standardized data structure and shared business definitions, it is difficult to evaluate which classes and programs are financially sustainable.

This project will build the foundation needed to analyze labor economics at the class and program level by standardizing dimensions across MB and QBO, preparing analysis-ready data, and defining metrics that support better business decisions.

## Project Objectives

1. Identify how mentor payroll, overhead, and other relevant labor costs are structured in QBO.
2. Determine how those financial fields can be linked to MB operational data.
3. Create a data dictionary that standardizes dimensions across both systems.
4. Build a clean, analysis-ready dataset for key business analysis.
5. Define and analyze metrics that evaluate labor economics and sustainability.
6. Deliver a report with findings, limitations, and recommendations.

## Core Business Questions

This repository is designed to help answer questions such as:

* What does it cost to run a class once mentor pay and overhead are considered?
* Which classes or class types are financially sustainable?
* How many attendees are needed for a class to break even?
* Which mentors or class types generate the strongest contribution margin?
* Which classes use studio time most efficiently?
* How should OOS think about pricing, scheduling, and compensation based on the data?

## Initial Analytical Scope

### Systems in scope

* **Mindbody**
* **QuickBooks Online**

### Mindbody datasets currently expected

* `attendance_analysis`
* `attendance_with_revenue`
* `sales`
* `detailed_visit_information`

### QuickBooks datasets to define

Examples may include:

* payroll detail
* labor expense exports
* P&L detail
* transaction detail by account
* chart of accounts
* classes/program-related revenue or cost allocations

## Key Metrics

### Foundation metrics

* **Direct Labor Cost per Class**
  Mentor pay associated with an individual class session.

* **Allocated Overhead Cost per Studio Hour**
  Total overhead cost for a selected period divided by total studio hours used in that period.

* **Allocated Overhead Cost per Class**
  Overhead cost per studio hour multiplied by class duration.

* **Contribution Margin per Class**
  `Revenue - Direct Labor Cost - Allocated Overhead Cost`

* **Break-Even Attendance**
  `(Direct Labor Cost per Class + Allocated Overhead Cost per Class) / Average Revenue per Attendee`

### Useful business metrics

* **Fully Loaded Cost as a % of Revenue**
* **Average Contribution Margin per Class by Class Type and Mentor**
* **Contribution Margin per Studio Hour**
* **Fully Loaded Cost as a % of Revenue by Class Type / Program Type**

## Working Assumptions

These assumptions should be validated as the project progresses:

* MB and QBO use inconsistent naming conventions that need standardization.
* A mapping layer or data dictionary will be necessary before reliable joins can happen.
* Some financial allocations may need to be estimated or proxied before a final methodology is agreed upon.
* Time windows may need to focus on either the most recent 12 months or the most recent two full seasons.
* Some programs may need to be analyzed separately from standard weekly classes.

## Repository Structure

```text
on-one-studios-data-analysis/
│
├── README.md
├── .gitignore
├── LICENSE
│
├── docs/
│   ├── project-overview.md
│   ├── scope-of-work-summary.md
│   ├── stakeholder-notes.md
│   ├── methodology.md
│   └── final-report.md
│
├── data/
│   ├── raw/
│   │   ├── mindbody/
│   │   └── qbo/
│   ├── interim/
│   ├── processed/
│   └── data-dictionary/
│       ├── field_inventory.csv
│       ├── dimension_mapping.csv
│       └── business_definitions.md
│
├── sql/
│   ├── extraction/
│   ├── cleaning/
│   ├── joins/
│   ├── metrics/
│   └── validation/
│
├── notebooks/
│   ├── 01_data_inventory.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_dimension_mapping.ipynb
│   ├── 04_metric_builds.ipynb
│   └── 05_analysis_and_visuals.ipynb
│
├── dashboards/
│   ├── tableau/
│   └── exports/
│
├── visuals/
│   ├── charts/
│   └── presentation/
│
└── issues_log/
    └── cleaning_issues_log.md
```

## Suggested GitHub README Sections

As the repository evolves, the README should eventually include:

1. Project overview
2. Business problem
3. Stakeholders
4. Data sources
5. Methodology
6. Data cleaning and standardization process
7. Metrics and KPI definitions
8. Key findings
9. Limitations
10. Recommendations
11. Next steps

## Recommended Workflow

### Phase 1 — Project setup

* Define repository structure
* Add scope and business context
* Log stakeholder questions
* List required datasets and missing fields

### Phase 2 — Data inventory

* Gather raw exports from MB and QBO
* Catalog every field available
* Identify primary keys, date fields, revenue fields, labor fields, and program descriptors

### Phase 3 — Data dictionary and standardization

* Standardize naming conventions
* Map equivalent dimensions across MB and QBO
* Create shared business definitions for classes, programs, mentors, sessions, products, and time periods

### Phase 4 — Data preparation

* Clean missing and duplicate records
* Resolve naming inconsistencies
* Build join-ready and analysis-ready datasets
* Document assumptions and unresolved issues

### Phase 5 — Analysis

* Calculate class-level and program-level economics
* Test profitability metrics
* Compare class types, mentors, and time periods
* Explore schedule efficiency and break-even thresholds

### Phase 6 — Communication

* Create visuals and dashboards
* Write findings and limitations
* Build a stakeholder-facing summary or presentation

## Early Deliverables to Build First

To make this GitHub useful quickly, prioritize these files first:

### 1. `README.md`

The main project page with context, scope, objectives, and repository guide.

### 2. `docs/project-overview.md`

A clearer narrative version of the business problem and why the work matters.

### 3. `docs/methodology.md`

How the project will connect MB and QBO data, what assumptions are being made, and what analysis steps will be followed.

### 4. `data/data-dictionary/business_definitions.md`

Shared definitions for metrics, class types, programs, mentor roles, time periods, and allocation methods.

### 5. `issues_log/cleaning_issues_log.md`

A running log of missing data, naming confusion, unclear fields, and decisions made during cleaning.

## Initial Notes on Analytical Direction

Based on project planning, this repository should likely emphasize:

* financial-operational linkage rather than isolated reporting
* business definitions before heavy analysis
* class/program economics rather than only descriptive attendance trends
* transparent assumptions and limitations
* stakeholder-ready interpretation, not just technical outputs

## Future Enhancements

As the project matures, this repository can expand to include:

* a formal KPI dictionary
* automated SQL pipelines
* Tableau dashboards
* season-over-season trend views
* mentor-level profitability summaries
* membership and package mix analysis
* room utilization and revenue-per-studio-hour analysis

## Status

**Current stage:** repository foundation and project framing

Next priority:

1. finalize the README
2. define the repo structure
3. inventory available MB and QBO datasets
4. start the data dictionary

---

## About This Repository

This repository is intended to function as both:

1. a working analysis environment for the OOS data project
2. a portfolio-quality case study showing structured business analytics work from scoping to insights
