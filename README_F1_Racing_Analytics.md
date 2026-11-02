# F1 Racing Analytics -- Tableau Project

## Project Overview

This project uses Tableau to explore Formula 1 racing data and present
useful insights through worksheets and an interactive dashboard. The
analysis focuses on drivers, teams, seasons, race results, circuits, lap
times, tyre compounds, podiums, and pit stops (if pit-stop data is
available).

## Objectives

-   Compare driver and team championship performance.
-   Explore race results and race-winning performance.
-   Analyze lap times, sector times, and speed-trap data.
-   Compare tyre-compound usage and average lap times.
-   Present key findings in a clear Tableau dashboard.

## Tools

-   **Tableau** -- data visualization and dashboard creation.
-   **F1 dataset** -- source data containing tables such as
    `race_results`, `championship_standings`, and `lap_intelligence`.
    Other tables, such as `pit_stops`, may be used if included in the
    dataset.

## Worksheets / Analysis

The project plan includes these views:

1.  Team Championship Points
2.  Team Championship Points -- Alternate View (keep only if it provides
    a different insight)
3.  Driver Championship
4.  Season-wise Champion
5.  Team Performance by Points
6.  Race Results Count
7.  Circuit-wise Race Analysis
8.  Driver Podium Analysis
9.  Fastest Lap Time by Driver
10. Tyre Compound Usage
11. Average Lap Time by Tyre Compound
12. Pit Stop Analysis (only if pit-stop data is available)
13. Sector Performance
14. Average Finishing Position
15. Race Status Distribution
16. Pole Positions by Driver
17. Driver Race Wins
18. Season-wise Race Performance

> **Note:** These are the worksheet ideas discussed during project
> planning. Some views may overlap. Keep the final workbook focused on
> distinct, correct insights rather than including every sheet just to
> increase the count.

## Key Tableau Field Setups

  -----------------------------------------------------------------------------
  Analysis          Dimension         Measure                 Recommended chart
  ----------------- ----------------- ----------------------- -----------------
  Team points       Team              `SUM(Points)`           Bar

  Driver            Driver (Champion) `SUM(Champion)`         Bar
  championships                                               

  Season champion   Season, Driver    No measure required for Text table
                    (Champion)        a name-by-season table  

  Circuit analysis  Circuit           `COUNT(Race ID)` or     Bar
                                      `COUNTD(Race ID)`       

  Podium analysis   Driver            `SUM(Podiums)`          Bar

  Fastest lap       Driver            `MIN(Lap Time S)`       Bar

  Tyre usage        Tyre Compound     `COUNT(Lap Number)`     Bar

  Average tyre lap  Tyre Compound     `AVG(Lap Time S)`       Bar
  time                                                        

  Sector            Driver            `AVG(Sector 1 S)`       Bar
  performance                         (repeat for sectors 2   
                                      and 3)                  

  Finishing         Driver            `AVG(Position)`         Bar
  position                                                    

  Race status       Status            `COUNT(Race ID)`        Bar

  Pole positions    Driver            `SUM(Pole Positions)`   Bar

  Season race       Season            `COUNT(Race ID)`; color Stacked bar
  performance                         by Driver               
  -----------------------------------------------------------------------------

## Important Notes and Data Checks

-   Use fields from the correct source table. For example, lap-time and
    sector-time analysis should use `lap_intelligence`.
-   For fastest lap time, use **`MIN(Lap Time S)`**. A lower time is
    faster.
-   For average lap time, use **`AVG(Lap Time S)`**, not `SUM`.
-   For average finishing position, a lower value is better. Check how
    non-finishes and missing positions are represented before
    interpreting the average.
-   `COUNT(Race ID)` counts non-null records; it may count driver-result
    rows rather than unique races. Use `COUNTD(Race ID)` when the goal
    is to count distinct races.
-   A race-wins chart must count only first-place results. If using a
    filter, drag `Position` from `race_results` to the Filters shelf and
    select the value representing first place (often `1`). Without that
    filter, name the chart **Race Results** or **Race Performance**, not
    **Race Wins**.
-   A pit-stop worksheet can only be built if the dataset contains a
    pit-stop table or equivalent fields.
-   Confirm that `Pole Positions` and `Podiums` are present and
    represent the intended totals before using them.

## Data Relationships

When creating Tableau relationships, match fields that represent the
same information and have compatible data types.

Examples: - `race_results.Season` ↔ `championship_standings.Season` -
`Driver` ↔ `Driver`, if both fields use the same driver names and naming
convention

Avoid connecting unrelated fields such as `Season` to
`Driver (Champion)`. Check data types too: Number should match Number,
String should match String, and Date should match Date. Do not rely on
data type alone; the values must also mean the same thing.

## Dashboard Recommendation

Create a dashboard named **F1 Racing Analytics Dashboard**.

Suggested layout: - **Top:** Dashboard title and KPI cards (Total Races,
Drivers, Teams, Circuits), if those counts are available and correctly
calculated. - **Middle:** Driver Championship and Team Performance. -
**Bottom:** Fastest Lap, Podium Analysis, Tyre Performance, and Race
Status. - **Filters:** Season, Driver, and Team, where they work
correctly across the selected charts.

## How to Use

1.  Open the Tableau workbook.
2.  Confirm that the data source is connected and all required tables
    are available.
3.  Check relationships and data types.
4.  Open each worksheet and verify its fields, aggregation, title, and
    sorting.
5.  Remove duplicate or misleading worksheets.
6.  Build the dashboard and test filters.
7.  Save the Tableau workbook as `.twb` or `.twbx`.

## Limitations

The exact dataset schema and values have not been independently
validated in this README. Field names may differ in your file, and some
planned tables or fields may not exist. Verify every worksheet against
the actual Data pane and source records before submission.

## Author

Add your name, course, section, college, and submission date here.
