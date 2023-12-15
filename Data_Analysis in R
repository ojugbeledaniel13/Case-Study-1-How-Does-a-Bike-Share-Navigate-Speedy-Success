 ## installing and loading the required Packages   

install.packages("tidyverse")
library(tidyverse)
install.packages("lubridate")
install.packages("lubridate")
library(lubridate)
install.packages("ggplot2")
library(ggplot2)

 ## getting working directory
 
getwd()

 ## setting working directory
 
setwd("C:/Users/USER/Documents/danielojugbele/Divvy Exercise/csv")

setwd("C:/Users/USER/Desktop/Divvy Exercise/csv")

getwd()

 ## importing  data to data-frame in R and viewing it
 
library(readr)
df1<-read_csv("202004-divvy-tripdata.zip")
View(df1)
library(readr)
df2<-read_csv("202005-divvy-tripdata.zip")
View(df2)
library(readr)
df3<-read_csv("202006-divvy-tripdata.zip")
View(df3)
library(readr)
df4<-read_csv("202007-divvy-tripdata.zip")
View(df4)
library(readr)
df5<-read_csv("202008-divvy-tripdata.zip")
View(df5)
library(readr)
df6<-read_csv("202009-divvy-tripdata.zip")
View(df6)
library(readr)
df7<-read_csv("202010-divvy-tripdata.zip")
View(df7)
library(readr)
df8<-read_csv("202011-divvy-tripdata.zip")
View(df8)
library(readr)
df9<-read_csv("202012-divvy-tripdata.zip")
View(df9)
library(readr)
df10<-read_csv("202101-divvy-tripdata.zip")
View(df10)
library(readr)
df11<-read_csv("202102-divvy-tripdata.zip")
View(df11)
library(readr)
df12<-read_csv("202103-divvy-tripdata.zip")
View(df12)


 ## Merging data into a single data frame 
 
bikerides<-rbind(df1,df2,df3,df4,df5,df6,df7,df8,df9,df10,df11,df12)
dim(bikerides)
 ## installing and loading janitor processing the data
install.packages("janitor")
library(janitor)

 ## cleaning and preparing data
 
bikerides<-janitor::remove_empty(dat = bikerides, which = c("cols"))
bikerides<-janitor::remove_empty(data= bikerides, which = c(rows))
bikerides<-janitor::remove_empty(dat= bikerides, which = c(rows))
bikerides<-janitor::remove_empty(data= bikerides, which = c(rows))
bikerides<-janitor::remove_empty(data= bikerides, which = c("rows"))
bikerides<-janitor::remove_empty(dat= bikerides, which = c("rows"))
dim(bikerides)

 ## converting started at and end at columns to date data types 

bikerides$started_at<-lubridate::as_datetime(bikerides$started_at)
bikerides$end_at<-lubridate::as_datetime(bikerides$end_at)
bikerides$ended_at<-lubridate::as_datetime(bikerides$ended_at)

 ## Getting the start time and end time components from data_time
 
bikerides$start_hr<-lubridate::hour_datetime(bikerides$started_at)
bikerides$start_hr<-lubridate::hour(bikerides$started_at)
bikerides$end_hr<-lubridate::hour(bikerides$ended_at)

 ## Getting the start and end date
 
bikerides$start_date<-lubridate::date(bikerides$started_at)
bikerides$end_date<-lubridate::date(bikerides$ended_at)

 ## Getting the ride length and changing diff date to numeric format, the duration is in seconds
 
bikerides$length_hr<-difftime(bikerides$ended_at, bikerides$started_at, units=c("hours"))
bikerides$length_hr<-as.numeric(bikerides$length_hr)

 ## changing diff date to numeric
 
bikerides$length_hr<-as.numeric(bikerides$length_hr)

 ## Getting the trip duration in mins
 
bikerides$length_min<-difftime(bikerides$ended_at, bikerides$started_at, units=c("mins"))
bikerides$length_min<-as.numeric(bikerides$length_min)

 ## I am now removing row which have a trip duration equal to or less than zero
 
bikerides_v2<-na.omit(bikerides[!(bikerides$start_station_name=="HQQR"|bikerides$length<=0),])
rlang::last_trace()
rlang::last_trace(drop = FALSE)
bikerides_v2<-na.omit(bikerides[!(bikerides$start_station_name =="HQ QR" | bikerides$length<=0),])
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$length<=0 ),])
rlang::last_trace()
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$length<=1 ),])
rlang::last_trace()
View(bikerides)
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$length<=10 ),])
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$length <= 0), ])
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$duration <= 0), ])
str(bikerides)
bikerides_v2 <- na.omit(bikerides[!(bikerides$start_station_name == "HQ QR" | bikerides$length_min <= 0), ])
dim(bikerides_v2)
colSums(is.na(bikerides_v2))

 ## Now i will assign days of the week to start and end date
 
bikerides_v2$start_day <- wday(bikerides_v2$start_date, label = TRUE, abbr = FALSE)
bikerides_v2$end_day <- wday(bikerides_v2$end_date, label = TRUE, abbr = FALSE)
       dim(bikerides_v2)
        View(bikerides_v2)
        
 ## i export the end of the result as csv to nwork on Tableau
 
write.csv(bikerides_v2, "gproject.csv", row.names = FALSE)
write.csv(bikerides_v2, "google project 1.csv", row.names = FALSE)

 ## i get the average trim duration as well as the maximum trip duration 
 
cat('average duration of rides is : ', mean(bikerides_v2$length_min), "mins")
cat('  maximum duration of rides is : ', round(max(bikerides_v2$length_min)/60/24), "days")

 ## i view the final data set as bikerides
 
View(bikerides)
View(bikerides_v2)
