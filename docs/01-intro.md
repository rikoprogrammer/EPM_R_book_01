---
output: html_document
editor_options: 
  chunk_output_type: console
---

# Introduction to R 

This is an introductory module in which we will learn the basics of R/Rstudio from installation to loading your first data file into R. R is a high level language that was developed by statisticians and was meant for statisticians. The two statisticians who came up with the language are Rose Ihaka and Robert Gentleman from the University of Auckland Australia. 

Since its implementation it has gained popularity over time by find use cases in new emerging fields like Data Science and lately in the Pharmaceutical industry now sharing almost an equal place with SAS (Statistical Analysis System) which has been the standard programming language in the Pharma industry for a very long time.

What makes R powerful is the idea of packages which is simply a collection of functions and data that have been packaged in a way that makes it easy for use and share with the large community. You will learn how to install and load packages in this module. For those who will advance in the series, you might as well learn how to create them as well.

## R Basics

### Installation for both R and Rstudio

The best way to learn programming in any language is through practice, and R is no different, therefore, I highly recommend you download both R and Rstudio before proceeding to other sections of the book.

R is the programming language while Rstudio is an interface/editor that helps you to program in R. You can do without it but having it will greatly improve your productivity. There are a plethora of editors to choose from ranging from VS Code to the more modern ones like Positron but in this book I will be using Rstudio. You are free to explore other editors in your own free time.

Install R software: https://cran.r-project.org/bin/windows/base/

Install Rstudio: https://posit.co/download/rstudio-desktop/

### Introduction to Rstudio Interface

Familiarize with the Rstudio user interface which we will use heavily. There are other editors that you can use like VS code, but Rstudio is widely used in the industry.

Make use of the menu bar at the top to navigate between various tasks eg opening a new R script, restarting an R session among other activities.

The interface has four main panes - Editor pane, Console, Environment and History pane. We have several sub-panes within each of the main panes.

### Creating objects, assignment and naming things in R

Almost everything you will work with in R, is an object, from vectors, data frames, lists or even environments. To create an object in R, simply come up with a name to call your object and assign it some value. If you are familiar with other programming languages perhaps you know some rules for naming objects, but in case you don't know or want to refresh your memory here are a few suggestions;

- names should not begin with a number or a special character

- names should not have spaces

**N/B** - R is case sensitive by the way so Cow and cow are two different names.

For a more extensive advise on naming objects please refer to this style guide: https://web.stanford.edu/class/cs109l/unrestricted/resources/google-style.html

To assign a value to an object we use the assignment operator <- or =, though using the former operator is highly recommended.

If you want to write comments in R use the hash symbol #. Anything written after the hash symbol is not evaluated as code.


### Data types

We need to understand basic data types before delving into complicated data structures. This will serve as a foundation to our future analysis of data in various contexts. There are two main categories of data types, simple data types and compound data types. Simple data types include, character, numeric, Boolean, complex, and raw data types while complex data types include lists, data frames environments etc. We will not discuss the complex and raw data types as they are not useful in data science/data analysis tasks.

There are no true scalars in R, even what you might think to be a scalar is actually a vector of length one. Vectors will be the basing building blocks for constructing other data structures. We create them using various methods; the common ones being via the c() command, using seq() command, using the : notation, etc, see examples below.


``` r
# using the c() command

vector1 <- c(1,2,4,5,6,9)
vector1
```

```
## [1] 1 2 4 5 6 9
```

``` r
#using the seq() command

vector2 <- seq(1:10)
vector2
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

``` r
#use the : notation

vector3 <- 2:20
vector3
```

```
##  [1]  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
```

**Getting help**

We can get help on how to use a function within R by type ?function name or help(function name). For example if you want to inspect the seq() function to see what kind of arguments it takes just type ?seq(). You try it as a form of exercise.


#### Character data type

This contain text data. You enclose them with either single or double quotes.


``` r
animals <- c("Cow","Dog","Cat")
animals
```

```
## [1] "Cow" "Dog" "Cat"
```

``` r
names <- c("Oscar","Eric","Ashley")
names
```

```
## [1] "Oscar"  "Eric"   "Ashley"
```

``` r
#as an exercise you can try creating more character vectors
```

#### Numeric data type

We have two sub-classes under this data type; integer and double/float. Integers are whole numbers without the decimal part while doubles or floats contain decimals. To create them we simply assign them to a variable without quotation marks as below.


``` r
# create an integer

int_numbers <- c(4L, 3L, 2L, 1L)
int_numbers
```

```
## [1] 4 3 2 1
```

``` r
# create a float

float_numbers <- c(3.24, 1.1, 0.54)
float_numbers
```

```
## [1] 3.24 1.10 0.54
```


#### Boolean data type

This data type results from asking logical questions, is x less than 2? The answer is either ```TRUE``` or ```FALSE```. Those values must be written in capital as shown and without quotation marks.


``` r
logical_vec <- c(TRUE, FALSE, TRUE, TRUE, FALSE)
logical_vec
```

```
## [1]  TRUE FALSE  TRUE  TRUE FALSE
```

``` r
# create a numeric vector and check whether each element in the vector is greater than 5. This will create for you a logical vector

x <- c(5, 1, 4, 10, 6)

logical_vec2 <- x > 5
logical_vec2
```

```
## [1] FALSE FALSE FALSE  TRUE  TRUE
```

To check the data type of any vector in R we use the ```mode()``` function.


``` r
mode(vector1)
```

```
## [1] "numeric"
```

``` r
mode(animals)
```

```
## [1] "character"
```

``` r
mode(logical_vec)
```

```
## [1] "logical"
```



### R packages

A brief introduction to what packages are, how to install and load them into the system. (we will not cover how to make your own package at this stage yet). An R package is a fundamental unit of R code, with a package you can easily share your work with other people who might be interested in using functions within your package. Its basically a collection of functions and data meant to perform certain specific tasks.

Most R packages are hosted on CRAN (Comprehensive R Archive Network), though we have other hosting places for R packages like Github or BioConductor. For our purposes in this book we shall only use packages from CRAN and in few cases use packages from GitHub.

There are two ways of installing packages; either via the graphical user interface in Rstudio or by writing code within R.

If we want to install via code we simply issue the command below either in the console or in an R script.


``` r
install.packages('package_name')

# package_name is the actual name of the package you want to install
```


### Data Import from various sources

How do you get your data into the R system. There are various ways of achieving this. We shall sample few methods. We have R base functions for achieving this and we also have functions from packages like readr or haven that we can use. To follow a long you will need some data saved locally on your computer, to simplify things make sure the data you have is comma separated (csv) file. A quick place to get some data sets for use is the kaggle website: https://www.kaggle.com/datasets. Save the data in your current working directory for easier access. In case you don't know how to set a working directory simply type ```getwd()``` in the console to see where your current directory is and if you want to change it simply issue the command ```setwd("specify the path to the desired folder using either double backslashes or single forward slashes")``` e.g ```setwd("D:/old data/LEARN/Clinical SAS/Readings")```.


``` r
# to load the csv file into R simply use read.csv command

my_data <- read.csv("filename.csv") #where filename is the actual name of your file

# this will load the data into memory and assign it to an an object called my_data. This object is formally called a data frame in R.
```

We can use related functions to import Excel files, SPSS files, SAS files etc. The ```haven``` and the ```readr``` packages provide modern functions that makes it easy to import as well as to write files from various systems. We will look at them in more detail in chapters three and four.

### Exercises







