# The US is Losing China's Pork Market 
Pork as one of the major US export sector now faces threats. Trump's recent decision to raise the tariff to an unprecedented level has pushed US' trade partners to retaliate even harsher. As one of the top pork buyers, China imposed a new round of tariff on US goods, including pork. The stakes are high for the U.S. pork industry under a volatile relationship between the U.S. and China.

Here is the shortcut to my [article:](https://yatingw24.github.io/exports/)

Data:
- [Market Share in Chinese Pork Imports](http://stats.customs.gov.cn/indexEn)
- [USDA Foreign Agricultural Service](https://apps.fas.usda.gov/GATS/default.aspx) 


## Key Takeaways 
Except for Business PhDs, stipends in other disciplines fall below the 2024 U.S. median cost of living ($3,851/month) and are quickly drained by basic expenses;

Students in Humanities, Arts and Social Sciences can hardly earn a stipend that would catch up with candidates in STEM and Business majors for almost a decade;

A PhD student's stipend is not necessarily tied to their year in the program;

## Questions That This Article Would Answer:
1. What are the reason(s) students in non-STEM disciplines receive fewer stipend? Has this been a trend for a long time before union strikes and even before Covid?
2. What does a Humanity PhD candidate's budget looks like after the deduction of living cost? 
3. Is there a decrease/increase in doctoral enrollments in disciplines such as Humanities, Arts and Social Science in recent years?
4. Are PhD students more or less financially struggling depending on which discipline he chooses?

## What I Did:
### Tech Stack sed:
 - `python - pandas`
 - `Datawrapper`
 - `JavaScript`
 - `regex`
 - `csv`

### A Break Down of Files:
 - `Analysis.ipynb`: the jupyter notebook where I did my majority of data cleaning and analysis.
  - `ggplot_dist.ipynb`: the jupyter notebook where I used R console to generate charts and plots. 
 - `cleaned_output.csv`: the curated dataset after my categorization of majors into four disciplines - Business, Science, Social Science and Humanities. 
 - `debt.csv`: a breakdown of percentage of debt by discipline.
  - `treemap.csv`: a spreadsheet which eventually presented through a treemap that shows the total number of doctoral enrollments in 2024 by discipline. 
 - `phd_stipends.csv`: the original dataset that contains all financial information about nationalwide stipends across discipines. 
 - static_imgs: charts and graphics you find in my article.
  - `privater.csv` and `public.csv`: data about English PhD stipends in public universities and private universities. 

### Data Cleaning and Analysis 
#### Part I: Understanding the Stipend Gap Between Disciplines



#### Part II: Educational Debt by Discipline
1. Calculated the percentage of debted students for each discipline using spreadsheet mathematic formulas. 

#### Part III: The Comparison Between Stipend Offered by Private and Public Universities
1. Since I'd like to practice data analysis and cleaning in R, I loaded the data in R;
2. Replaced all signs, such as the dollar sign $, and converted the stipend into numeric numbers using `mutate()` function in R. Here is a sample code:

```python 
public %>%
  mutate(
    `Amount_USD` = gsub(",", "", `Amount_USD`),   
    `Amount_USD` = gsub("\\$", "", `Amount_USD`), 
    `Amount_USD` = as.integer(`Amount_USD`)       
  )

  ```
3. Combined the dataframe for private schools and public schools together using `rbind()`.
4. Stacked density plots for each type of university to compared the gap between the median English PhD stipend. 

### Visuals
#### 1st -  
1. Converted the `cleaned_output.csv` into a dataframe and make multiple boxplots to the distribution of **median stipend** by discipline and by time. As the statistical summary revealed, each discipline's stipend is more or less normally distributed. Either median and mean could be a fair representation of the overall stipend. 
![Chart](static_imgs/boxplot.png)
2. Named a new dataframe called `df_median` grouped by `Academic Year` and `Field`. `summarize()` is used to ensure all data entries are median stipend for a specific major in a specific academic year.
3. Made **a multi-line chart** using `geom_rect`, `geom_line` and `geom_point`. 
4. A breakdown of chart elements:
- each line: each line representing a discipline: Business, Social Science, STEM, and Humanities;
- x-axis: the academic year;
- y-axis: median stipend in $;
- highlighted area: academic years affected by the pandemic.

#### 2nd - 
1. Loaded the data, `debt.csv` and went straight to making ggplot using `geom_bar`.
2. Given that I'd like to represent the percentage, I need to have the bar background go to 100%. As a result, I required `library(scales)` and set my my x-axis' scale from 0 to 1.
3. Colored each major accordingly to the disciple each belongs to and made sure the title matches the color-coding as well. 
4. a breakdown of chart elements:
- x-axis: the percentage of debted students;
- y-axis: The major.

#### 3rd -


#### 4th - 


## Limitations & Things I'd Like to Improve
1. This is a data-driven project done with a limited amount of time - I would interview PhD candidates from public universities to understand their stipend and how they support themselves financially;
2. While this analysis compares stipends to the U.S. median cost of living ($3,851/month in 2024), the actual living costs vary widely by location. Future work could involve curating a new dataset on regional stipend differences and visualizing geographic disparities in financial support for PhD students. 
3. While I applied a stipend range filter (15,000–90,000), I could have used more systematic outlier detection methods, such as boxplots or IQR filtering to assess the impact of extreme values.
 

 
