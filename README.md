# School_District_Analysis

Analysis on student standardised test scores and school fundings using Anaconda and Jupyter Notebook

## Overview
Maria, a chief data scientist at City School District responsible for analysing school data needs our help with analysing student funding and student standardised test scores. For this, we aggregated the data and found trends in school data which helped in discussions and make strategic decisions at school and district level. We used Anaconda and Jupyter Notebook for performing this analysis.

The school data, which was given to us in 2 csv files, were merged into one complete file, scrutinized for any missing data and a summary report was build showing performance of each school with its average math and reading score, passing percentage in math and reading and overall student passing percentage. We also ran summary report based on school size, school budget and type of school.

Now, we need to address an issue which was brought to the school board regarding academic dishonesty by Thomas High School specifically for its 9th grade students. With this new revelation. We need to remove all the incorrect scores (replace them with NaN) for Thomas High School 9th grade students, and update summary reports to show the actual numbers to the board.

## Results

### How is the district summary affected?

Original summary

![image](https://user-images.githubusercontent.com/108366412/181427756-02c59ece-d627-446d-bc4d-ce4d1f2279ad.png)
 
The grades for Thomas High School 9th grade students (491 students) were changed to NaN after which new district summary was ran. Loc function was used to replace the values to NaN. student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "reading_score"] = np.nan

Adjusted summary

![image](https://user-images.githubusercontent.com/108366412/181427818-5ec8dd6b-3775-437c-a5c6-a84ba7862ccf.png)

From the numbers we can see there is a nominal change in the passing percentage of 0.2%, 0.1% and 0.3% in math, reading and overall percentages respectively. Data of 491 students was changed out of a pool of 39170 students. Thus, only minor difference in passing percentages can be seen which if rounded off to zero decimal, may not show any difference in the adjusted summary. The number of students and total budget remained as is as they were run on the original school data which was unchanged. 

### How is the school summary affected?

Grades of 491 students from Thomas High School 9th grade were replaced with NaN which led to the updated school summary. A huge drop in passing percentage in math, reading and overall passing can be seen. Passing Math % dropped from 93.27% to 66.91%, reading from 97.31% to 69.66% and overall % dropped from 90.95% to 65.08% respectively.

Original Thomas High School summary

![image](https://user-images.githubusercontent.com/108366412/181428069-c71e8e40-e99c-471d-a06a-af14b12e8504.png)

Adjusted Thomas High School summary

![image](https://user-images.githubusercontent.com/108366412/181428082-a1061342-f37b-455c-afd9-8f854845b394.png)

### How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

With the 9th grade scores replaced to NaNs (keeping student count as is), the overall passing percentage for Thomas High School dropped from 90.95% to 65.08% which led to its rank dropping from 2nd to 8th position. Once we updated the number of students to just 10th, 11th and 12th grade students, we were able to get updated ranking which shows Thomas High School is back at 2nd position with overall percentage of 90.63%

Original Ranking

![image](https://user-images.githubusercontent.com/108366412/181428228-50590bfb-bb76-4012-89ed-48533ec9ea22.png)

Ranking including 9th grade with NaN and total student id

![image](https://user-images.githubusercontent.com/108366412/181428261-b1b1ba66-6b41-4deb-aa1d-2db7a0ba8de6.png)

Ranking excluding 9th grade

![image](https://user-images.githubusercontent.com/108366412/181428365-6fbbf0ee-a147-42a6-bf59-75c80dba58d3.png)

### How does replacing the ninth-grade scores affect the following:

  * Math and reading scores by grade
  
    Average scores for all the grades for all schools remain the same except the 9th grade scores for Thomas High School which were at 83.7 for reading and 83.6 for math. Now both these values are replaced by nan. 

Original and adjusted math average scores

![image](https://user-images.githubusercontent.com/108366412/181428674-a34cc60e-94af-4eb3-a984-6e2a20900637.png)  ![image](https://user-images.githubusercontent.com/108366412/181428819-a9478592-b23c-42c1-91a7-e604dc4c6a94.png) 

Original and adjusted reading average scores

![image](https://user-images.githubusercontent.com/108366412/181428971-97520155-fe83-40f1-92be-e5877fd047a3.png)  ![image](https://user-images.githubusercontent.com/108366412/181428996-7176b43c-c54a-40a0-bd4b-cb0eec00bc01.png)

  * Scores by school spending
    Thomas High School is part of the 631-645 spending group which is nominally affected by the removal of the 9th grade scores. From the below images we can see that originally the overall passing percentage is 62.86% which is updated to 62.78%. This difference can only be found at the tenth place. Data seems to remain same when we are rounding off the percentages to zero decimal points. 

Original scores by school spending
![image](https://user-images.githubusercontent.com/108366412/181429369-19857405-9f31-4186-888d-7afdd25cfe8a.png)

Adjusted scores by school spending
![image](https://user-images.githubusercontent.com/108366412/181429457-cef90b2e-57ff-4c5c-8c50-64dc0fef7763.png)

  * Scores by school size
    
    The school size summary seems unchanged from the rounded percentages. However, minute differences can be seen in medium size schools (1000-1999) at the hundredth place where the overall percentage of passing students was at 90.62% in original and 90.56% in the updated database.

Original scores by school size
![image](https://user-images.githubusercontent.com/108366412/181429568-68e95452-5a48-4d66-8509-42e26d84ae1b.png)

Adjusted scores by school size
![image](https://user-images.githubusercontent.com/108366412/181429579-1ef12666-3d37-4eeb-bb58-4a12366431ad.png)

  * Schools by school type

    The Charter school type seems to be affected at the hundredth place with overall passing percentage falling from 90.43% to 91.39%. A similar difference can be seen in math and reading percentage with a difference of 0.01% and 0.03% respectively. 

Original scores by school type
![image](https://user-images.githubusercontent.com/108366412/181429655-0dec8098-93d4-47d9-9ec5-f3c7a5fc6c1c.png)

Adjusted scores by school type
![image](https://user-images.githubusercontent.com/108366412/181429668-6d1cdbbb-2e1a-4f08-8c30-5788e26929e4.png)

## Summary

### Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.

  * At school level, the overall performance of Thomas High School was affected by the removal of 9th grade scores. The overall students passing dropped from 90.95% to 65.08%.
  * Passing percentages for math and reading dropped down to 66.91% (from 93.27%) and 69.66% (from 97.31%) 
  * The average math and reading scores for 9th grade at school level for Thomas High School were replaced with nan.
  * Thomas High School dropped from 2nd position to 8th position in terms of overall passing percentages. However, when considering just 10th, 11th and 12th grade, it was back to its 2nd position among all schools.
