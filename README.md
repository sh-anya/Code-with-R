# Quick Reference - R Programming

### Installing a new package

```
> install.packages("package_name")
> install.packages("gplots")
```

### Checking version of a package 

```
> packageVersion("package_name")
> packageVersion("gplots")
```

### Assignment operators

a) Leftwards assignment <- , <<- , =<br/>
b) Rightwards assignment -> , ->> <br/>
<- and = assign to variables in the same environment. <br/>
<<- assigns to variables in global environments.<br/>

```
> name <- some_value
> x <- 10 

     (OR)

> 10 -> x
```
This example will create a single element numeric vector.

### Accepting user input

```
> x <- readline(prompt="Message ... ")
> x <- readline(prompt="Enter a number of your choice :")
```	

### Data Types

5 basic datatypes

	1) character
	2) numeric (real/decimal)
	3) integer (Use L to indicate R that the value has to be stored as integer)
	4) logical (boolean)
	5) complex (a+ib)

### Data Structures

	1) vectors (contains data elements of same type)
	2) list
	3) matrix
	4) data frame
	5) factors

### Creating a vector, default datatype is 'logical'

```
> vector()
  OR
> vector("datatype", length=n)

> vector("integer", length=5) #This creates a vector with 5 elements & default integer value 0.
```

### How to create the vectors using the constructors? 

We can use numeric, character, logical


```
> constructor(length)


> character(6) 
  [1] ""  ""  ""  ""  ""  ""

> numeric(4)
  [1] 0 0 0 0 

> logical(2)
  [1] FALSE  FALSE
```

### Creating vectors using c() 

We can create vectors by concatenating the elements.

```
> c(item1, item2, ... ,item-n)

> c(1, 3, 5, 7, 9) #integer vector
> c(1.1, 1.3, 1.5, 1.7, 1.9) #numeric vector
> c(TRUE, FALSE, FALSE) #logical vector
> c("a", "b", "c") #character vector
> c(1+2i, 1+3i, 1+5i) #complex vector
```

### Thumb rule of Vectors & Coercion 

A vector does not allow us to have values of mixed types. What happens when we give values of mixed type like the following? 

```
> c(1.5, "ananya", 2, TRUE) 

[1] "1.5" "johny" "2" "TRUE" 
```
Whooo! What happened? 
R has converted all the values into character mode. This is called 'coercion'. When R does it by itself, that's implicit coercion. What if we want to change it explicitly, then as.* functions are handy. 

```
> as.*(vector) 

> x <- 1:4 #will produce 1 2 3 4 
> as.character(x) 
  [1] "1" "2" "3" "4" 
```

What if R cannot figure out to which mode the vector has to be changed. Hmm, then it just results in NA with a warning. 

```
> x <- c("a", "n", "a", "n", "y", "a") 
> as.integer(x) #Now R says, I don't know what to do...!! 

[1] NA NA NA NA NA NA 
Warning: NAs introduced by coercion
```

### Using seq() and creating vectors of numbers.

```
> seq(begin, end, increment_by)

> seq(0, 5, 0.5) 
  [1] 0.0   0.5   1.0   1.5   2.0   2.5   3.0   3.5   4.0   4.5   5.0
```

### Difference between is.na() and anyNA()

is.na( ) returns TRUE for each element of the vector if the element is a NA, else FALSE <br/>
anyNA( ) returns TRUE if the vector has a NA(missing value)

NA indicates a missing value, NaN indicates Not a Number.

```
> x <- c("A", "B", NA, "C", NA)

> is.na(x)
  [1] FALSE   FALSE   TRUE   FALSE   TRUE

> anyNA(x)
  [1] TRUE
```

### Checking the type of a vector. 

```
> typeof(vector)

> x <- 1:4	#will produce 1 2 3 4 
> typeof(x) 	 
[1]  "Integer"
```

### Checking length of a vector

```
> length(vector)

> x <- 1:4	#will produce 1 2 3 4 
> length(x)
  [1] 4
```

### We can use str() function to display the structure of an object.
This is not a type-casting function of strings.

```
> str(object)
> x <- c("a", "n", "a", "n", "y", "a") 
> str(x)
  chr  [1:6]  "a"  "n"  "a"  "n"  "y"  "a"
```

### Difference between nchar() and nzchar()

nchar() returns the size of a character vector. <br/>
nzchar() checks if elements of a character vector are non-empty strings.

```
> nchar(char_vector)
> nzchar(char_vector)

Example 1:
> x <- "ananya"
> nchar(x)
  [1] 6
> nzchar(x)
  [1] TRUE

Example 2:
> x <- c("banana", "apple", "orange")
> nchar(x) 
  [1]  6   5   6
> nzchar(x)
  [1]  TRUE   TRUE   TRUE

Example 3:
> x <- c("banana", "", "orange")
> nzchar(x)
  [1] TRUE   FALSE   TRUE
```

### Matrix- atomic vector with dimension, filled column wise

nrow = number of rows <br/>
ncol = number of columns

```
> matrix( nrow=n, ncol=m) 

Example 1: 
> x <- matrix(nrow=3, ncol=2)

		    [,1] [,2]
	[1,]   NA   NA
	[2,]   NA   NA
	[3,]   NA   NA

Example 2:
> x <- matrix(11:20, nrow=5, ncol=2)

	[,1]  [,2]
	[1,]   11   16
	[2,]   12   17
	[3,]   13   18
	[4,]   14   19
	[5,]   15   20
```

### Binding columns and rows using cbind() and rbind()

```
> rbind( seq1, seq2)
  OR
> cbind( seq1, seq2)

> a <- 11:20
> b <- 21:30

> rbind(a, b)
   [,1]    [,2]   [,3]   [,4]   [,5]
a    11     12     13     14     15
b    21     22     23     24     25

> cbind(a, b)
     a  b
[1,] 11 21
[2,] 12 22
[3,] 13 23
[4,] 14 24
[5,] 15 25
```


### Converting a vector to matrix

```
> x <- 11:20
> x
  [1] 11 12 13 14 15 16 17 18 19 20

> dim(x) <- c(5,2)
> x
	      [,1] [,2]
	[1,]   11   16
	[2,]   12   17
	[3,]   13   18
	[4,]   14   19
	[5,]   15   20
```

### Accessing Matrix elements using [row, column]

```
> x <- matrix(11:20, nrow=5, ncol=2, byrow=TRUE)

	     [,1]  [,2]
	[1,]   11   12
	[2,]   13   14
	[3,]   15   16
	[4,]   17   18
	[5,]   19   20

> x[2,2] #2nd row, 2nd column value
  [1] 14 
```

### Lists
As we saw with previous examples, we cannot store values of different types in one vector. What if we have to use values of different types in a data structure? We have "list" for that. 

To create a list of values we use list().

```
Example 1:
> x <- list(1, "Ananya", 5, "Data Analyst")
> x

[[1]]
[1] 1

[[2]]
[1] "Ananya"

[[3]]
[1] 5

[[4]]
[1] "Data Analyst"

Example 2: 
> x <- list()
> x[1] = 1
> x[2] = "Ananya"
> x[3] = 5
> x[4] = "Data Analyst"

> x
[[1]]
[1] 1

[[2]]
[1] "Ananya"

[[3]]
[1] 5

[[4]]
[1] "Data Analyst"

```
Did you notice something different in the above examples? If you have guessed it, that's superb... It's about indices. In R the index starts from 1, not 0. So, what happens if we try to add an element at index 0 to a list, or we try accessing the index 0 of a list? Let's see in the next example.

```
Example 3:

> x <- list()
> x[0] <- "Ananya"
> x
  list()

> x <- list(1, "Ananya", 5, "Data Analyst")
> x[[0]]
  Error in x[[0]] : 
  attempt to select less than one element in get1index <real>
```

### Naming list elements
```
> x <- list(emp_id=101, name="Ananya", desig="Data Analyst", exp="5+ years")
> x

$emp_id
[1] 101

$name
[1] "Ananya"

$desig
[1] "Data Analyst"

$exp
[1] "5+ years"

#To check the names of elements of list, we can use names()
> names(x)
  [1] "emp_id" "name"   "desig"  "exp" 
```

### Accessing list elements using index and name of the element.
To access the list element by index we use [[]], and by name we use $

```
> x <- list(emp_id=101, name="Ananya", desig="Data Analyst", exp="5+ years")
> x[[2]]
  [1] "Ananya"

> x$name
  [1] "Ananya"
```

### DataFrame

There are 3 ways to create a DataFrame.
1) Using data.frame() 
2) Using read.csv() 
3) Using read.table()

Here is the sample data

Employee Details - CSV file(data.csv)
![CSV_Data](/images/csv_data.png)

Employee Details - Text file(data.txt)
![TXT_Data](/images/data_text.png)

Let's create a DataFrame using above mentioned methods.

#### Method 1: Using data.frame()
``` 
> emp_data <- data.frame(EmpID = 101:105,
			 Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
			 Age = c(35, 30, 21, 40, 28),
			 Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"),
 			 Experience = c(7, 5, 0, 14, 2),
			 Income = c(2000000, 800000, 200000, 3000000, 500000),
			 Projects = c("more than two", "two", "", "multiple", "two"))

> emp_data

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
```

#### Method 2: Using read.csv()
```
> emp_data <- read.csv('data.csv')

> emp_data

  EmpID   Name Age    Designation Experience  Income          Projects
1   101 Ramesh  35        Manager          7 2000000  more than two   
2   102  Deepa  30         SDE-II          5  800000            two   
3   103 Raksha  21         Intern          0  200000                  
4   104   Prem  40 Senior Manager         14 3000000       multiple   
5   105 Akshay  28          SDE-I          2  500000            two
```

#### Method 3: Using read.table()
```
> emp_data <- read.table('data.txt', sep=",", header=TRUE)

> emp_data

 EmpID    Name Age     Designation Experience  Income          Projects
1   101  Ramesh  35         Manager          7 2000000  more than two   
2   102   Deepa  30          SDE-II          5  800000            two   
3   103  Raksha  21          Intern          0  200000                  
4   104    Prem  40  Senior Manager         14 3000000       multiple   
5   105  Akshay  28           SDE-I          2  500000            two
```

#### Some functions on DataFrame

```
> emp_data <- data.frame(EmpID = 101:110,
	Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay", "Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
	Age = c(35, 30, 21, 40, 28, 35, 30, 21, 40, 28),
	Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I", "Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"), Experience = c(7, 5, 0, 14, 2, 7, 5, 0, 14, 2),
	Income = c(2000000, 800000, 200000, 3000000, 500000, 2000000, 800000, 200000, 3000000, 500000),
	Projects = c("more than two", "two", "", "multiple", "two", "more than two", "two", "", "multiple", "two"))
```

```
> head(emp_data) #get first 6 rows.

    EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106 Ramesh  35        Manager          7  2e+06 more than two
```

```
> head(emp_data, n=2) #specify number of rows instead of 6

  EmpID   Name Age Designation Experience Income      Projects
1   101 Ramesh  35     Manager          7  2e+06 more than two
2   102  Deepa  30      SDE-II          5  8e+05           two
```

```
> tail(emp_data) #get last 6 rows.

   EmpID   Name Age    Designation Experience Income      Projects
5    105 Akshay  28          SDE-I          2  5e+05           two
6    106 Ramesh  35        Manager          7  2e+06 more than two
7    107  Deepa  30         SDE-II          5  8e+05           two
8    108 Raksha  21         Intern          0  2e+05              
9    109   Prem  40 Senior Manager         14  3e+06      multiple
10   110 Akshay  28          SDE-I          2  5e+05           two
```

```
> tail(emp_data, n=2) #specify number of rows instead of 6

   EmpID   Name Age    Designation Experience Income Projects
9    109   Prem  40 Senior Manager         14  3e+06 multiple
10   110 Akshay  28          SDE-I          2  5e+05      two
```

```
> names(emp_data) #get the column names of dataframe
  [1] "EmpID"       "Name"        "Age"         "Designation" "Experience" 
  [6] "Income"      "Projects" 
```

```
> colnames(emp_data) #get the column names of dataframe
  [1] "EmpID"       "Name"        "Age"         "Designation" "Experience" 
  [6] "Income"      "Projects" 
```

```
> str(emp_data) #structure of the dataframe. Note that this is not string conversion str() function.
   'data.frame':	10 obs. of  7 variables:
   $ EmpID      : int  101 102 103 104 105 106 107 108 109 110
   $ Name       : Factor w/ 5 levels "Akshay","Deepa",..: 5 2 4 3 1 5 2 4 3 1
   $ Age        : num  35 30 21 40 28 35 30 21 40 28
   $ Designation: Factor w/ 5 levels "Intern","Manager",..: 2 4 1 5 3 2 4 1 5 3
   $ Experience : num  7 5 0 14 2 7 5 0 14 2
   $ Income     : num  2e+06 8e+05 2e+05 3e+06 5e+05 2e+06 8e+05 2e+05 3e+06 5e+05
   $ Projects   : Factor w/ 4 levels "","more than two",..: 2 4 1 3 4 2 4 1 3 4
```

```
> dim(emp_data) #Dimension of the dataframe.
  [1] 10  7
```

```
> nrow(emp_data) #no. of rows
  [1] 10
```

```
> ncol(emp_data) #no. of columns
  [1] 7
```

```
> sapply(emp_data, class) #get the class of each column 
  EmpID        Name         Age Designation  Experience      Income 
  "integer"    "factor"   "numeric"    "factor"   "numeric"   "numeric" 
   
  Projects 
  "factor"
```

```
> is.data.frame(emp_data) #check if data frame
  [1] TRUE
```

```
> typeof(emp_data) #as dataframe is a special type of 'list'
  [1] "list"
```

```
> class(emp_data) 
  [1] "data.frame"
```

### Accessing Components of DataFrame 
```
> emp_data$Designation
  [1] Manager        SDE-II         Intern         Senior Manager SDE-I         
  [6] Manager        SDE-II         Intern         Senior Manager SDE-I         
  Levels: Intern Manager SDE-I SDE-II Senior Manager
```

```
> emp_data[['Designation']] 
  [1] Manager        SDE-II         Intern         Senior Manager SDE-I         
  [6] Manager        SDE-II         Intern         Senior Manager SDE-I         
  Levels: Intern Manager SDE-I SDE-II Senior Manager
```

```
> emp_data[2:6, ] #access like a matrix, row 2 to 6, all columns
  EmpID   Name Age    Designation Experience Income      Projects
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106 Ramesh  35        Manager          7  2e+06 more than two
```

```
> emp_data[, 2:3] #all rows, column 2 to 3
     Name Age
1  Ramesh  35
2   Deepa  30
3  Raksha  21
4    Prem  40
5  Akshay  28
6  Ramesh  35
7   Deepa  30
8  Raksha  21
9    Prem  40
10 Akshay  28
```

```
> emp_data[, 2]  #all rows, column 2
[1] Ramesh Deepa  Raksha Prem   Akshay Ramesh Deepa  Raksha Prem   Akshay
Levels: Akshay Deepa Prem Raksha Ramesh
```

When we extract only one column a vector is returned.
If we want to get it as rows/tabular form we can use 'DROP'
```
> emp_data[, 2, drop=FALSE]    
   Name
1  Ramesh
2   Deepa
3  Raksha
4    Prem
5  Akshay
6  Ramesh
7   Deepa
8  Raksha
9    Prem
10 Akshay
```

```
> emp_data[emp_data$Income<600000, ] #retrieving columns with conditions
   EmpID   Name Age Designation Experience Income Projects
3    103 Raksha  21      Intern          0  2e+05         
5    105 Akshay  28       SDE-I          2  5e+05      two
8    108 Raksha  21      Intern          0  2e+05         
10   110 Akshay  28       SDE-I          2  5e+05      two
```

### Modifying DataFrame Components
```
emp_data <- data.frame(EmpID = 101:105,
       Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
       Age = c(35, 30, 21, 40, 28),
       Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"),
       Experience = c(7, 5, 0, 14, 2),
       Income = c(2000000, 800000, 200000, 3000000, 500000),
       Projects = c("more than two", "two", "", "multiple", "two"), stringsAsFactors = FALSE)

> emp_data

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
```

#### Add a new row to dataframe using rbind()
```
> rbind(emp_data, list(106, "Sujan", 23, "SDE", 1, 300000, "one"))

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106  Sujan  23            SDE          1  3e+05           one
```

Did you notice the data.frame() function has one extra argument 'stringsAsFactors'? 
Why have we added that? OK, let's try the same example without adding it.

```
> emp_data <- data.frame(EmpID = 101:105,
       Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
       Age = c(35, 30, 21, 40, 28),
       Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"),
       Experience = c(7, 5, 0, 14, 2),
       Income = c(2000000, 800000, 200000, 3000000, 500000),
       Projects = c("more than two", "two", "", "multiple", "two"))

> emp_data

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two

> rbind(emp_data, list(106, "Sujan", 23, "SDE", 1, 300000, "one"))

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106   <NA>  23           <NA>          1  3e+05          <NA>
Warning messages:
1: In `[<-.factor`(`*tmp*`, ri, value = "Sujan") :
  invalid factor level, NA generated
2: In `[<-.factor`(`*tmp*`, ri, value = "SDE") :
  invalid factor level, NA generated
3: In `[<-.factor`(`*tmp*`, ri, value = "one") :
  invalid factor level, NA generated
```

We have a warning message and the last row has NA. Why did it happen on string/character type columns only? 
That is becasue of the default behavior of data.frame(), which forces the columns with character values to be Factors,</br> 
and the value we are trying to add here is not one of the levels of the factor. </br> 

For example, when emp_data was created the Name column was converted to Factor, which had defined levels as shown in the earlier example. (Refer to str(emp_data) above)<br/>
***$ Name : Factor w/ 5 levels "Akshay","Deepa",..: 5 2 4 3 1 5 2 4 3 1 <br/>***
The five names we have, "Ramesh", "Deepa", "Raksha", "Prem", "Akshay" were the defined levels.<br/>
When we tried to add a new record with name "Sujan", it was not one of the defined levels and hence <br/>
NA was added there with a warning.

The argument, stringsAsFactors when set to FALSE does not force the same. Thus, avoiding <NA> in those columns.

So, what happens if we try to rbind() the existing values from the defined levels of these factors. Let's see it with the example.

```
> emp_data <- data.frame(EmpID = 101:105,
       Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
       Age = c(35, 30, 21, 40, 28),
       Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"),
       Experience = c(7, 5, 0, 14, 2),
       Income = c(2000000, 800000, 200000, 3000000, 500000),
       Projects = c("more than two", "two", "", "multiple", "two"))

> rbind(emp_data, list(106, "Deepa", 23, "SDE-II", 1, 300000, "two"))

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106  Deepa  23         SDE-II          1  3e+05           two
```

rbind() successfully added a row without a warning. But this may not be the situation always,</br>where we get a chance to add a row with existing values from defined levels. What do we do?

Setting stringsAsFactors = FALSE is an easy way to solve this problem. 
What alternatives do we have?
We can convert columns to character type using as.character.

```
> emp_data <- data.frame(EmpID = 101:105,
       Name = c("Ramesh", "Deepa", "Raksha", "Prem", "Akshay"),
       Age = c(35, 30, 21, 40, 28),
       Designation = c("Manager", "SDE-II", "Intern", "Senior Manager", "SDE-I"),
       Experience = c(7, 5, 0, 14, 2),
       Income = c(2000000, 800000, 200000, 3000000, 500000),
       Projects = c("more than two", "two", "", "multiple", "two"))

> str(emp_data)
'data.frame': 5 obs. of  7 variables:
 $ EmpID      : int  101 102 103 104 105
 $ Name       : Factor w/ 5 levels "Akshay","Deepa",..: 5 2 4 3 1
 $ Age        : num  35 30 21 40 28
 $ Designation: Factor w/ 5 levels "Intern","Manager",..: 2 4 1 5 3
 $ Experience : num  7 5 0 14 2
 $ Income     : num  2e+06 8e+05 2e+05 3e+06 5e+05
 $ Projects   : Factor w/ 4 levels "","more than two",..: 2 4 1 3 4

> emp_data$Name <- as.character(emp_data$Name)
> emp_data$Designation <- as.character(emp_data$Designation)
> emp_data$Projects <- as.character(emp_data$Projects)

> str(emp_data)
'data.frame': 5 obs. of  7 variables:
 $ EmpID      : int  101 102 103 104 105
 $ Name       : chr  "Ramesh" "Deepa" "Raksha" "Prem" ...
 $ Age        : num  35 30 21 40 28
 $ Designation: chr  "Manager" "SDE-II" "Intern" "Senior Manager" ...
 $ Experience : num  7 5 0 14 2
 $ Income     : num  2e+06 8e+05 2e+05 3e+06 5e+05
 $ Projects   : chr  "more than two" "two" "" "multiple" ...

> rbind(emp_data, list(106, "Sujan", 23, "SDE", 1, 300000, "one"))

  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two
6   106  Sujan  23            SDE          1  3e+05           one
```

### Add a new column to dataframe using cbind()

```
> cbind(emp_data, Location=c("Bangalore", "Mangalore", "Chennai", "Bangalore", "Pune"))
  EmpID   Name Age    Designation Experience Income      Projects  Location
1   101 Ramesh  35        Manager          7  2e+06 more than two Bangalore
2   102  Deepa  30         SDE-II          5  8e+05           two Mangalore
3   103 Raksha  21         Intern          0  2e+05                 Chennai
4   104   Prem  40 Senior Manager         14  3e+06      multiple Bangalore
5   105 Akshay  28          SDE-I          2  5e+05           two      Pune
```

### Delete a column from DataFrame

Set the column/s to NULL to delete the column/s. OR reassign by dropping a column.
```
> emp_data$Location <- NULL
> emp_data
  EmpID   Name Age    Designation Experience Income      Projects
1   101 Ramesh  35        Manager          7  2e+06 more than two
2   102  Deepa  30         SDE-II          5  8e+05           two
3   103 Raksha  21         Intern          0  2e+05              
4   104   Prem  40 Senior Manager         14  3e+06      multiple
5   105 Akshay  28          SDE-I          2  5e+05           two

> emp_data[6:7] <- list(NULL)
> emp_data
  EmpID   Name Age    Designation Experience
1   101 Ramesh  35        Manager          7
2   102  Deepa  30         SDE-II          5
3   103 Raksha  21         Intern          0
4   104   Prem  40 Senior Manager         14
5   105 Akshay  28          SDE-I          2

> emp_data <- emp_data[, -1]
> emp_data
    Name Age    Designation Experience 
1 Ramesh  35        Manager          7  
2  Deepa  30         SDE-II          5  
3 Raksha  21         Intern          0  
4   Prem  40 Senior Manager         14  
5 Akshay  28          SDE-I          2

> emp_data <- emp_data[-1]
> emp_data
  Age    Designation Experience
1  35        Manager          7
2  30         SDE-II          5
3  21         Intern          0
4  40 Senior Manager         14
5  28          SDE-I          2
```

### Delete a row in DataFrame

```
> emp_data <- emp_data[-2, ]
> emp_data
  Age    Designation Experience
1  35        Manager          7
3  21         Intern          0
4  40 Senior Manager         14
5  28          SDE-I          2
```

### Factors

In the earlier examples of dataframes we had come across 'Factors'. So what are they? 
Factors are the data structures which we use for the fields taking only predefined values, i.e categorical values.
For example, categorical columns like, 
  - Loan Status (Approved/Not Approved)
  - Gender (Male/Female)
  - Marital Status (Married, Single) and so on..

The distinct values of factors are called as levels, and we would know the possible values in advance for these type of fields.

#### Creating factors

To create factors we use factor(), and if we do not mention the levels R infers from the given values. To specify the levels, factor() should be used with 'levels'

```
> marital_status <- factor(c("married", "unmarried", "unmarried", "married", "married"))

> marital_status
[1] married   unmarried   unmarried   married   married  
Levels: married unmarried

> marital_status <- factor(c("married", "unmarried", "unmarried", "married", "married"), levels=c("married", "unmarried", "divorced"))

> marital_status
[1] married   unmarried   unmarried   married   married  
Levels: married unmarried divorced
```

To check if a variable is a factor, we use is.factor(variable)

```
> is.factor(marital_status)
[1] TRUE
``` 

#### Get the levels of factor using levels()

```
> levels(marital_status)
[1] "married"   "unmarried" "divorced" 
```

When we look at the structure of a factor, there is something noticeable. 

```
> marital_status
[1] married   unmarried   unmarried   married   married  

> str(marital_status)
Factor w/ 3 levels "married","unmarried",..: 1 2 2 1 1
```

Did you notice the values? 1 2 2 1 1 
Yes, factors are stored as integer vectors.

#### How do we modify the factors?

In the earlier examples of dataframes, we have seen the warning that results in NA when we try to save a new value in factors.
Let's see an example, 
We have a variable loan_status which takes two values "approved" and "not approved". Now we want to add another value to this set of predefined values, "in process". 

```
> loan_status <- factor(c("approved", "not approved", "approved", "approved"))

> loan_status
[1] approved     not approved approved  approved    
Levels: approved not approved


> loan_status[1] <- "in process" #let's try modifying the first value
Warning message:
In `[<-.factor`(`*tmp*`, 1, value = "in process") :
  invalid factor level, NA generated
```

Does that mean we can not modify factors? No, that doesn't. 
To modify a factor, we need to add the new value to its levels first. 
Here is how we do that.

```
> levels(loan_status) <- c(levels(loan_status), "in process")
> loan_status[1] <- "in process"
> loan_status
[1] in process   not approved   approved     approved    
Levels: approved not approved in process
```

So, now we know about both dataframes and factors, let's get back to "stringsAsFactors = FALSE". The default behavior of data.frame() can be suppressed using stringsAsFactors = FALSE. i.e we can avoid data.frame() forcing any character type variables/columns being changed into factors. But, is it worth doing so? 

There might be many variables in the dataset which need to be retained as factors and in that case using stringsAsFactors = FALSE is not advisable.
Know the data and then use what is necessary. 

To be continued... 
