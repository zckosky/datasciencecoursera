Question 1The American Community Survey distributes downloadable data about United States communities. Download the 2006 microdata survey about housing for the state of Idaho using download.file() from here: 

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv

and load the data into R. The code book, describing the variable names is here:

https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf 

Create a logical vector that identifies the households on greater than 10 acres who sold more than $10,000 worth of agriculture products. Assign that logical vector to the variable agricultureLogical. Apply the which() function like this to identify the rows of the data frame where the logical vector is TRUE.  

which(agricultureLogical) 

What are the first 3 values that result?

```
  fileURL <- "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv"
  dat <- tbl_df(read.csv(fileURL, header=TRUE))
  dat2 <- datdat %>%         
                mutate(id = seq(1:6496), result = (ACR %in% 3 & AGS %in% 6)) %>%        
                select(id,ACR,AGS,result) %>%        
                filter(result == T) %>%        
                head(3)
```

 A tibble: 3 x 4                
id   ACR   AGS result                
<int> <int> <int> <lgl>                 
1   125     3     6 T                     
2   238     3     6 T                     
3   262     3     6 T 
                
```                
  agriculturalLogical <- dat2$ACR == 3 & dat2$AGS == 6
  which(agriculturalLogical)[1:3]                
```

[1] 125 238 262
