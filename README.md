# Vocal-Range-Analysis
This repository has been created to analyze how the height of a singer is a significant correlating factor in determining the vocal range of the singer.


# Problem Statement
Consider the dataset stored in the file singer.txt. It contains heights in inches of the singers in the New York Choral Society in 1979. The data are grouped according to the voice part. There are four voice parts, namely, Bass, Tenor, Alto, and Soprano. The vocal range for each voice part increases in pitch from Bass to Soprano. Perform an exploratory analysis of the data by examining the distributions of the heights of the singers in the four groups.


# Analysis (R Code)

#This is a program to analyze the data present in the data set 'Singer.txt'. 
#Converting the .txt file to a .csv file and importing it into RStudio
library(readr)
singer <- read_csv("D:/FALL 17 MSCS/CS 6313.002 STATS/MINI PROJECTS/singer.csv")

#Exploratory Analysis of data using functions
#Summary
summary(singer)
#Histogram
hist(singer$height, xlab = "Height Range of Singers", ylab = "Frequency of heights", main = "Histogram of Singer data set", prob = TRUE)
#Estimating if the heights of the singers follow a Normal Distribution
curve(dnorm(x, mean = mean(singer$height), sd = sd(singer$height)), add = TRUE)

#Using 'by' function
by(singer$height,singer$voice.part,mean)
by(singer$voice.part,singer$height,summary)
#Other Data Exploratory functions
names(singer)
head(singer)
tail(singer)
str(singer)
boxplot(singer$height)
dim(singer)

#Using 'subset' function
Bassvoicepart = subset(singer, singer$voice.part=="Bass")
summary(Bassvoicepart)
hist(Bassvoicepart$height)
boxplot(Bassvoicepart$height)

Tenorvoicepart = subset(singer, singer$voice.part=="Tenor")
summary(Tenorvoicepart)
hist(Tenorvoicepart$height)
boxplot(Tenorvoicepart$height)

Altovoicepart = subset(singer, singer$voice.part=="Alto")
summary(Altovoicepart)
hist(Altovoicepart$height)
boxplot(Altovoicepart$height)

Sopranovoicepart = subset(singer, singer$voice.part=="Soprano")
summary(Sopranovoicepart)
hist(Sopranovoicepart$height)
boxplot(Sopranovoicepart$height)


#Making subsets of singers based on 3 height ranges: 60-65, 65-70 and 70-76
Height1 = subset(singer, singer$height < 65 & singer$height >=60)
summary(Height1)
Height2 = subset(singer, singer$height < 70 & singer$height >=65)
summary(Height2)
Height3 = subset(singer, singer$height <=76 & singer$height >=70)
summary(Height3)

hist(singer$height)
