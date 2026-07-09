# Python_Portfolio
This is the portfolio of python code that I learned during Bisc 450C

## Analyzing patient data ( 1, 2, and 3 are all together)

This is analysis, we looked at inflammation data for multiple patients


```python
import numpy
```

```python
numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```


    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])






```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```

```python
print(data)
```
    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]




```python
print(type(data))
```
    <class 'numpy.ndarray'>




```python
print(data.shape)
```
    (60, 40)




```python
print('first value in data:' , data [0,0])
```
    first value in data: 0.0




```python
print('middle value in data:', data[29,19])
```
    middle value in data: 16.0




```python
print(data[0:4, 0:10])
```
    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]




```python
print(data[5:10, 0:10])
```
    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]




```python
small = data[:3,36:]
```

```python
print('small is:')
```
    small is:




```python
print(small)
```
    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]




```python
# Lets us a numpy function
print(numpy.mean(data))
```
    6.14875




```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
print('maximum inflammation:', maxval)
print('minimum inflammation:', minval)
print('standard deviation', stdval)
```
    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation 4.613833197118566




```python
# Sometimes we want to look at variation in statistical valus, such as maximum inflammation per patient,
# or average from day one.

patient_0 = data[0,:] # 0 on the first axis (rows), everything on the second (columns)

print('maximum inflammation for patient 0:', numpy.amax(patient_0))
```
    maximum inflammation for patient 0: 18.0




```python
print('maximum inflammation for patient 2:', numpy.amax(data[2, :]))
```
    maximum inflammation for patient 2: 19.0




```python
print(numpy.mean(data, axis = 0))
```
    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]




```python
print(numpy.mean(data, axis = 0).shape)
```
    (40,)




```python
print(numpy.mean(data, axis = 1))
```
    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]


# Creating functions (1, 2, 3, and 4 are all together)

```python
import numpy
```

```python
numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```


    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])






```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```

```python
print(data)
```
    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]




```python
print(type(data))
```
    <class 'numpy.ndarray'>




```python
print(data.shape)
```
    (60, 40)




```python
print('first value in data:' , data [0,0])
```
    first value in data: 0.0




```python
print('middle value in data:', data[29,19])
```
    middle value in data: 16.0




```python
print(data[0:4, 0:10])
```
    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]




```python
print(data[5:10, 0:10])
```
    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]




```python
small = data[:3,36:]
```

```python
print('small is:')
```
    small is:




```python
print(small)
```
    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]




```python
# Lets us a numpy function
print(numpy.mean(data))
```
    6.14875




```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```

```python
print(maxval)
print(minval)
print(stdval)
```
    20.0
    0.0
    4.613833197118566




```python
print('maximum inflammation:', maxval)
print('minimum inflammation:', minval)
print('standard deviation', stdval)
```
    maximum inflammation: 20.0
    minimum inflammation: 0.0
    standard deviation 4.613833197118566




```python
# Sometimes we want to look at variation in statistical valus, such as maximum inflammation per patient,
# or average from day one.

patient_0 = data[0,:] # 0 on the first axis (rows), everything on the second (columns)

print('maximum inflammation for patient 0:', numpy.amax(patient_0))
```
    maximum inflammation for patient 0: 18.0




```python
print('maximum inflammation for patient 2:', numpy.amax(data[2, :]))
```
    maximum inflammation for patient 2: 19.0




```python
print(numpy.mean(data, axis = 0))
```
    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]




```python
print(numpy.mean(data, axis = 0).shape)
```
    (40,)




```python
print(numpy.mean(data, axis = 1))
```
    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]



# Python Fundametals 

```python
# Any python interpreter can be used as a calculator:
3 + 5 * 4
```


    23






```python
# Lets save a value to a variable
weight_kg = 60
```

```python
print(weight_kg)
```
    60




```python
# Weight0 = valid
# 0weight = invalid
# weight and Weight are different
```

```python
# Types of data
# There are three common types of data
# Integer numbers
# floating point numbers
# Strings

```

```python
# Floating point number
weight_kg = 60.3
```

```python
# String comprised of Letters
patient_name = "Jon Smith"
```

```python
# String comprised of numbers
patient_id = '001'
```

```python
# Use variables in python

weight_lb = 2.2 * weight_kg 

print(weight_lb)
```
    132.66




```python
# Lets add a prefix to our patient id

patient_id = 'inflam_' + patient_id

patient_id
```


    'inflam_001'






```python
# Lets combine print statements

print(patient_id, 'weight in kilograms:', weight_kg)
```
    inflam_001 weight in kilograms: 60.3




```python
# we can call a function inside another function

print(type(60.3))

print(type(patient_id))
```
    <class 'float'>
    <class 'str'>




```python
# we can also do calculations inside the print function

print('weight in lbs:', 2.2 *weight_kg)
```
    weight in lbs: 132.66




```python
print(weight_kg)
```
    60.3




```python
weight_kg = 65.0
print('weight in kilograms is now:', weight_kg)
```
    weight in kilograms is now: 65.0




```python

```

# Loops

```python
odds = [1,3,5,7]
```

```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])

```
    1
    3
    5
    7




```python
odds = [1,3,5]
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```
    1
    3
    5



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-3-01ba67d8a9e5> in <module>
          3 print(odds[1])
          4 print(odds[2])
    ----> 5 print(odds[3])
    

    IndexError: list index out of range




```python
odds = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]

for num in odds: 
        print(num)
```
    1
    3
    5
    7
    9
    11
    13
    15
    17
    19




```python
length = 0
names = ['Curie', 'Darwin', 'Turing']
for value in names:
    length = length + 1
print('There are', length, 'names in the list')    
```
    There are 3 names in the list




```python
name = "Rosalind"
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('after the loop, name is', name)
```
    Curie
    Darwin
    Turing
    after the loop, name is Turing




```python
print(len([0,1,2,3]))
```
    4




```python
name = ['Curie', 'Darwin', 'Turing']

print(len(name))
```
    3




```python

```

# Defensive Programming

```python
numbers = [1.5, 2.3, 0.7, 0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```
    total is: 8.901




```python
def normalize_rectangle(rect):
    """Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.
    input should be of the format (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively"""
    assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'
    
    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = dy / dx
        upper_x, upper_y = scaled
    else:
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0
        
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'
    
    return (0, 0, upper_x, upper_y)
```

```python
print(normalize_rectangle( (0.0, 1.0, 2.0) ))
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-7-f9d109085db1> in <module>
    ----> 1 print(normalize_rectangle( (0.0, 1.0, 2.0) ))
    

    <ipython-input-6-5e167894086a> in normalize_rectangle(rect)
          3     input should be of the format (x0, y0, x1, y1).
          4     (x0, y0) and (x1, y1) define the lower left and upper right corners of the rectangle respectively"""
    ----> 5     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
          7     assert x0 < x1, 'Invalid X coordinates'


    AssertionError: Rectangles must contain 4 coordinates




```python
print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
```

    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-8-f7e0d48bdfd0> in <module>
    ----> 1 print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
    

    <ipython-input-6-5e167894086a> in normalize_rectangle(rect)
          5     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
    ----> 7     assert x0 < x1, 'Invalid X coordinates'
          8     assert y0 < y1, 'Invalid Y coordinates'
          9 


    AssertionError: Invalid X coordinates




```python
print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0) ))
```
    (0, 0, 0.2, 1.0)




```python
print(normalize_rectangle( (0.0, 0.0, 5.0, 1.0) ))
```

    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-10-8d4a48f1d068> in <module>
    ----> 1 print(normalize_rectangle( (0.0, 0.0, 5.0, 1.0) ))
    

    <ipython-input-6-5e167894086a> in normalize_rectangle(rect)
         12     if dx > dy:
         13         scaled = dx / dy
    ---> 14         upper_x, upper_y = scaled
         15     else:
         16         scaled = dx / dy


    TypeError: cannot unpack non-iterable float object




```python

```

# Multiple Files

```python
import glob
```

```python
print(glob.glob('inflammation*.csv'))
```
    ['inflammation-10.csv', 'inflammation-09.csv', 'inflammation-11.csv', 'inflammation-06.csv', 'inflammation-05.csv', 'inflammation-08.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-04.csv', 'inflammation-03.csv', 'inflammation-02.csv', 'inflammation-12.csv']




```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]

for filename in filenames:
    print(filename)
    
    data = numpy.loadtxt(fname=filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize = (10.0, 3.0))
    
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data, axis = 0))
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data, axis = 0))
    
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data, axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```
    inflammation-01.csv




![png](output_2_1.png)

    inflammation-02.csv




![png](output_2_3.png)

    inflammation-03.csv




![png](output_2_5.png)

```python

```

```python

```

```python

```

# Storing values in lists

```python
odds = [1, 3, 5, 5]
print('odds are:', odds)
```
    odds are: [1, 3, 5, 5]




```python
print('first element:', odds[0])
print('last element:', odds[3])
print('"-1" element, odds[-1]')
```
    first element: 1
    last element: 5
    "-1" element, odds[-1]




```python
names = ['Curie', 'Darwing', 'Turing'] # Typo in Darwin's name

print('names is originally:', names)

names[1] = 'Darwin' # Correct the name

print('final value of names:', names)
```
    names is originally: ['Curie', 'Darwing', 'Turing']
    final value of names: ['Curie', 'Darwin', 'Turing']




```python
#name = 'Darwin'
#name[0] = 'd'
```

```python
odds.append(11)
print('odds after adding a value:', odds)
```
    odds after adding a value: [1, 3, 5, 5, 11]




```python
removed_element = odds.pop(0)
print('odds after removing the first element:', odds)
print('removed_element:', removed_element)
```
    odds after removing the first element: [3, 5, 5, 11]
    removed_element: 1




```python
odds.reverse()
print('odds after reversing:', odds)
```
    odds after reversing: [11, 5, 5, 3]




```python
odds = [3,5,7]
primes = odds
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```
    primes: [3, 5, 7, 2]
    odds: [3, 5, 7, 2]




```python
odds = [3,5,7]
primes = list(odds)
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```
    primes: [3, 5, 7, 2]
    odds: [3, 5, 7]




```python
binomial_name = "Drosophila melanogaster"
group = binomial_name[0:10]
print('group:', group)

species = binomial_name[11:23]
print('species:', species)

chromosomes = ['X', 'Y', '2', '3', '4']
autosomes = chromosomes[2:5]
print('autosomes:', autosomes)

last = chromosomes[-1]
print('last:', last)
```
    group: Drosophila
    species: melanogaster
    autosomes: ['2', '3', '4']
    last: 4




```python
date = 'Monday 4 January 2023'
day = date[0:6]
print('Using 0 to begin range:', day)
day = date[:6]
print('omitting beginning index:', day)
```
    Using 0 to begin range: Monday
    omitting beginning index: Monday




```python
months = ['jan', 'feb', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep','oct', 'nov', 'dec']
sond = months[8:18]
print('With knwn last position:', sond)

sond = months[8:len(months)]
print('Using len() to get last entry:', sond)

sond = months[8:]
print('Omitting ending index:', sond)
```
    With knwn last position: ['sep', 'oct', 'nov', 'dec']
    Using len() to get last entry: ['sep', 'oct', 'nov', 'dec']
    Omitting ending index: ['sep', 'oct', 'nov', 'dec']




```python

```

# Transcribing DNA into RNA

```python
# Prompt the user to enter the input file name

input_file_name = input("Enter the name of the input fasta file: ")
```

```python
# Open the input fasta file and read the DNA sequence

with open(input_filename_, "r") as input_file:
    dna_sequence = ""
    for line in input_file:
        if line.startswith(">"):
            continue
        dns_sequence += line.strip()
```

```python
# Transcribe the DNA to RNA
rna_sequence = ""
for nucleotide in dna_sequence:
    if nucleotide == "T":
        rna_sequence += "U"
    else:
        rna_sequence += nucleotide
```

```python
# Prompt the user to enter the output file name

out_file_name = input("Enter the name of the output file: ")
```

```python
# Save the RNA sequence to a text file

with open(output_file_name, "w") as output_file:
    output_file.write(rna_sequence)
    print(f"The RNA sequence has been saved to {output_file_name})")
```

```python
print(rna_sequence)
```

```python

```

# Using Juypter Notebooks 1 and 2

{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "%matplotlib inline\n",
    "import pandas as pd\n",
    "import matplotlib.pyplot as plt\n",
    "import seaborn as sns\n",
    "sns.set(style = \"darkgrid\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "df = pd.read_csv('/home/student/Desktop/classroom/myfiles/notebooks/fortune500.csv')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Year</th>\n",
       "      <th>Rank</th>\n",
       "      <th>Company</th>\n",
       "      <th>Revenue (in millions)</th>\n",
       "      <th>Profit (in millions)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <td>0</td>\n",
       "      <td>1955</td>\n",
       "      <td>1</td>\n",
       "      <td>General Motors</td>\n",
       "      <td>9823.5</td>\n",
       "      <td>806</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>1</td>\n",
       "      <td>1955</td>\n",
       "      <td>2</td>\n",
       "      <td>Exxon Mobil</td>\n",
       "      <td>5661.4</td>\n",
       "      <td>584.8</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>2</td>\n",
       "      <td>1955</td>\n",
       "      <td>3</td>\n",
       "      <td>U.S. Steel</td>\n",
       "      <td>3250.4</td>\n",
       "      <td>195.4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>3</td>\n",
       "      <td>1955</td>\n",
       "      <td>4</td>\n",
       "      <td>General Electric</td>\n",
       "      <td>2959.1</td>\n",
       "      <td>212.6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>4</td>\n",
       "      <td>1955</td>\n",
       "      <td>5</td>\n",
       "      <td>Esmark</td>\n",
       "      <td>2510.8</td>\n",
       "      <td>19.1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Year  Rank           Company  Revenue (in millions) Profit (in millions)\n",
       "0  1955     1    General Motors                 9823.5                  806\n",
       "1  1955     2       Exxon Mobil                 5661.4                584.8\n",
       "2  1955     3        U.S. Steel                 3250.4                195.4\n",
       "3  1955     4  General Electric                 2959.1                212.6\n",
       "4  1955     5            Esmark                 2510.8                 19.1"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Year</th>\n",
       "      <th>Rank</th>\n",
       "      <th>Company</th>\n",
       "      <th>Revenue (in millions)</th>\n",
       "      <th>Profit (in millions)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <td>25495</td>\n",
       "      <td>2005</td>\n",
       "      <td>496</td>\n",
       "      <td>Wm. Wrigley Jr.</td>\n",
       "      <td>3648.6</td>\n",
       "      <td>493</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>25496</td>\n",
       "      <td>2005</td>\n",
       "      <td>497</td>\n",
       "      <td>Peabody Energy</td>\n",
       "      <td>3631.6</td>\n",
       "      <td>175.4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>25497</td>\n",
       "      <td>2005</td>\n",
       "      <td>498</td>\n",
       "      <td>Wendy's International</td>\n",
       "      <td>3630.4</td>\n",
       "      <td>57.8</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>25498</td>\n",
       "      <td>2005</td>\n",
       "      <td>499</td>\n",
       "      <td>Kindred Healthcare</td>\n",
       "      <td>3616.6</td>\n",
       "      <td>70.6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>25499</td>\n",
       "      <td>2005</td>\n",
       "      <td>500</td>\n",
       "      <td>Cincinnati Financial</td>\n",
       "      <td>3614.0</td>\n",
       "      <td>584</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "       Year  Rank                Company  Revenue (in millions)  \\\n",
       "25495  2005   496        Wm. Wrigley Jr.                 3648.6   \n",
       "25496  2005   497         Peabody Energy                 3631.6   \n",
       "25497  2005   498  Wendy's International                 3630.4   \n",
       "25498  2005   499     Kindred Healthcare                 3616.6   \n",
       "25499  2005   500   Cincinnati Financial                 3614.0   \n",
       "\n",
       "      Profit (in millions)  \n",
       "25495                  493  \n",
       "25496                175.4  \n",
       "25497                 57.8  \n",
       "25498                 70.6  \n",
       "25499                  584  "
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.tail()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [],
   "source": [
    "df.columns = ['year', 'rank', 'company', 'revenue', 'profit']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>year</th>\n",
       "      <th>rank</th>\n",
       "      <th>company</th>\n",
       "      <th>revenue</th>\n",
       "      <th>profit</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <td>0</td>\n",
       "      <td>1955</td>\n",
       "      <td>1</td>\n",
       "      <td>General Motors</td>\n",
       "      <td>9823.5</td>\n",
       "      <td>806</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>1</td>\n",
       "      <td>1955</td>\n",
       "      <td>2</td>\n",
       "      <td>Exxon Mobil</td>\n",
       "      <td>5661.4</td>\n",
       "      <td>584.8</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>2</td>\n",
       "      <td>1955</td>\n",
       "      <td>3</td>\n",
       "      <td>U.S. Steel</td>\n",
       "      <td>3250.4</td>\n",
       "      <td>195.4</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>3</td>\n",
       "      <td>1955</td>\n",
       "      <td>4</td>\n",
       "      <td>General Electric</td>\n",
       "      <td>2959.1</td>\n",
       "      <td>212.6</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>4</td>\n",
       "      <td>1955</td>\n",
       "      <td>5</td>\n",
       "      <td>Esmark</td>\n",
       "      <td>2510.8</td>\n",
       "      <td>19.1</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   year  rank           company  revenue profit\n",
       "0  1955     1    General Motors   9823.5    806\n",
       "1  1955     2       Exxon Mobil   5661.4  584.8\n",
       "2  1955     3        U.S. Steel   3250.4  195.4\n",
       "3  1955     4  General Electric   2959.1  212.6\n",
       "4  1955     5            Esmark   2510.8   19.1"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "25500"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "len(df)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "year         int64\n",
       "rank         int64\n",
       "company     object\n",
       "revenue    float64\n",
       "profit      object\n",
       "dtype: object"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>year</th>\n",
       "      <th>rank</th>\n",
       "      <th>company</th>\n",
       "      <th>revenue</th>\n",
       "      <th>profit</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <td>228</td>\n",
       "      <td>1955</td>\n",
       "      <td>229</td>\n",
       "      <td>Norton</td>\n",
       "      <td>135.0</td>\n",
       "      <td>N.A.</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>290</td>\n",
       "      <td>1955</td>\n",
       "      <td>291</td>\n",
       "      <td>Schlitz Brewing</td>\n",
       "      <td>100.0</td>\n",
       "      <td>N.A.</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>294</td>\n",
       "      <td>1955</td>\n",
       "      <td>295</td>\n",
       "      <td>Pacific Vegetable Oil</td>\n",
       "      <td>97.9</td>\n",
       "      <td>N.A.</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>296</td>\n",
       "      <td>1955</td>\n",
       "      <td>297</td>\n",
       "      <td>Liebmann Breweries</td>\n",
       "      <td>96.0</td>\n",
       "      <td>N.A.</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <td>352</td>\n",
       "      <td>1955</td>\n",
       "      <td>353</td>\n",
       "      <td>Minneapolis-Moline</td>\n",
       "      <td>77.4</td>\n",
       "      <td>N.A.</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     year  rank                company  revenue profit\n",
       "228  1955   229                 Norton    135.0   N.A.\n",
       "290  1955   291        Schlitz Brewing    100.0   N.A.\n",
       "294  1955   295  Pacific Vegetable Oil     97.9   N.A.\n",
       "296  1955   297     Liebmann Breweries     96.0   N.A.\n",
       "352  1955   353     Minneapolis-Moline     77.4   N.A."
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "non_numeric_profits = df.profit.str.contains('[^0-9.-]')\n",
    "df.loc[non_numeric_profits].head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "{'N.A.'}"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "set(df.profit[non_numeric_profits])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "369"
      ]
     },
     "execution_count": 15,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "len(df.profit[non_numeric_profits])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "bin_sizes, _, _ = plt.hist(df.year[non_numeric_profits], bins= range(1955, 2006))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [],
   "source": [
    "df = df.loc[~non_numeric_profits]\n",
    "df.profit = df.profit.apply(pd.to_numeric)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "25131"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "len(df)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "year         int64\n",
       "rank         int64\n",
       "company     object\n",
       "revenue    float64\n",
       "profit     float64\n",
       "dtype: object"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [],
   "source": [
    "group_by_year = df.loc[:, ['year', 'revenue', 'profit']].groupby('year')\n",
    "avgs = group_by_year.mean()\n",
    "x = avgs.index\n",
    "y1 = avgs.profit\n",
    "def plot(x, y, ax, title, y_label):\n",
    "    ax.set_title(title)\n",
    "    ax.set_ylabel(y_label)\n",
    "    ax.plot(x, y)\n",
    "    ax.margins(x = 0, y = 0)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAbMAAAELCAYAAABTdGifAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAgAElEQVR4nOzdd1xUV/o/8M/0YeiDdLFiQVGKA3axdyzRRGNMYs0as9FU180m1uwvX0viJhuNiRqy2c2mWFZFTUxTE41dUbGLKEhvAwzlTju/P5ALo5QZGBhmeN6vly9hzsydcw8z88w557nnCBhjDIQQQogdE9q6AoQQQkhjUTAjhBBi9yiYEUIIsXsUzAghhNg9CmaEEELsHgUzQgghdo+CWRNZsGAB/ve//9m6GoTYrfPnz2P06NGIiIjAzz//bNX31KZNm9C3b18MHDjQKscjLQCzoWHDhrETJ07YsgrEArNnz2ahoaEsPDyc/3fhwoUGH+u7776zcg3Ns3v3bta9e3eT8zh16hRfnpqaymbPns169+7NxowZ89hrNC4ujg0YMIBFRkay5cuXM47jmvsUWoXnnnuOffHFFzWW7d69m82cObNBx01PT2e9evViubm5jaleg3Ecx15++WU2bNgw1rVrV5PXHmOMFRYWsmXLlrF+/fqxfv36sY8++sikfNiwYaxXr178a3fu3Ll8WX2v7epSU1NZ165dmU6na9B5XLx4kc2ZM4dFRUWxvn37spdffpllZWXx5Uajka1fv55FR0ez6Ohotm7dOmY0Gvnya9eusalTp7LevXuzqVOnsmvXrvFlH330EevRo4fJeaSkpNRZH4frmen1eltXwaGtWLECFy9e5P9FRERY9HjGGIxGYxPVznzh4eEm59G3b1++7PXXX0ePHj1w+vRpvPrqq1iyZAny8/MBAL///js+++wzfPHFF/j111/x4MEDfPTRR7Y6Dbtlzvs0PT0dXbp0sfpzp6WlwcPDA15eXjWWN8dnSGRkJNavXw9vb+/Hyt577z2UlZXh119/xc6dO7Fv3z7s3r3b5D5bt27lX7uff/65SVldr21rKiwsxFNPPYVff/0VR44cgbOzM/7617/y5d9++y1+/vln7Nu3D/v378fRo0fxzTffAAC0Wi0WL16MSZMm4ezZs5gyZQoWL14MrVbLP37cuHEm5xEUFFRnfVpMMNuzZw+efvpprFu3DlFRURg+fDiOHTvGl6vVavz1r3/FoEGDEBUVhcWLFwMATp8+jSFDhuCzzz7DwIED+cY8cuQIJk+eDJVKhZkzZ+LGjRv8sT777DOMHDkSERERGD9+PH766Se+7P79+5g9ezb69OmDvn374pVXXuHLkpKSMHfuXERHR2PMmDE4dOhQrefz7LPPYufOnWad26OGDx+O7du3IzY2FuHh4XjrrbeQm5uLBQsWICIiAnPmzEFhYSF//4SEBMycORMqlQqTJk3C6dOn+bLdu3dj3LhxiIiIwIgRI/gXU/W2+/zzz9G/f38MGjTosTeNuS5cuIBp06ahT58+mDZtGi5cuGDSFps2bcLMmTMRFhaGN998E+fOncOaNWsQERGBNWvW4MGDB+jWrZvJB4klbVhcXIy33noLgwYNwuDBg7Fp0yYYDAaLzyM5ORlXr17Fyy+/DLlcjjFjxqBr1644fPgwAGDv3r2YPn06unTpAnd3dyxevLjOoa9z587xf5uYmBjs2bOHr++yZcvQr18/DBs2DFu2bOGD/J49ezBz5kz8v//3/6BSqTBixAhcuHABe/bsQUxMDPr372/ynMuXL8eKFSswd+5cREREYPbs2UhLS+PL3333XcTExCAyMhJPPPEEzp07x5f985//xNKlS7Fs2TJERERgwoQJuHLlCgBg+/btePnll03OZ+3atfj73/9e47kOHz4cn376KcaPH4+oqCj89a9/BcdxAGp/n3733XcYNWoUoqOjsWjRImRlZQEARo4cidTUVCxatAgRERHQarX86yEpKQkrV65EQkICIiIioFKpAADHjh3D+PHjERERgcGDB2PHjh2P1fGPP/7AvHnzkJ2djYiICCxfvpx/7e3cuRNDhw7F888/DwD45ZdfMGHCBKhUKjz77LNISkoyOVdL3qPVSaVSzJkzByqVCkLh4x/Bv/76KxYsWAAnJye0bdsW06dPb/D7si6zZ88GAERFRSEiIgIXL16E0WjEli1bMGzYMPTv3x/Lli1DcXFxjY+PiYnBuHHj4OLiAicnJ8yePdvkfb93717MmzcPfn5+8PX1xdy5c/nX7ZkzZ6DX6/H8889DKpXiueeeA2MMp06davgJNah/aSXVhxl3797NevTowb799lum1+vZV199xQYOHMh3SxcuXMiWLl3K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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "fig, ax = plt.subplots()\n",
    "plot(x, y1, ax, 'Increase in mean Fortune 500 company profits from 1955 to 2005', 'Profit(millions)')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAboAAAELCAYAAACvYUNVAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAgAElEQVR4nOzdeVxTV/o/8E8SCDuE3YC4o2IpCARwAVGwIoqoo1bqWOvW1tpxa6u1tgWrTvtDHa1Otdq6dNr6ra3LoKhVW1Grti6ouKGiiIrsW1gCJCQ5vz8YL0YFw5oEnvfrxetFcu5NnvvkJk/Oyb338BhjDIQQQkgbxdd1AIQQQkhLokJHCCGkTaNCRwghpE2jQkcIIaRNo0JHCCGkTaNCRwghpE2jQqcDM2fOxH//+19dh0GIwbp48SKGDRsGHx8f/P777836nlq7di0CAwMxcODAZnk8ogeYnhoyZAg7c+aMrsMgWpo8eTLz9PRkffv25f4uXbrU6Mf65ZdfmjlC7ezZs4f17t1bYzvOnj3LtWdkZLDJkyczLy8vFh4e/sw+un37djZgwADm6+vLFi9ezORyeWtvQrswZcoU9t133z23bc+ePSw6OrpRj5uVlcVefvllVlBQ0JTwGk0ul7M5c+awIUOGsJ49e2rse4wxVlJSwhYtWsT69evH+vXrx9avX6/RPmTIEPbyyy9z++60adO4thft20/KyMhgPXv2ZNXV1Y3ajsuXL7OpU6cyf39/FhgYyObMmcNyc3O5drVazVauXMkCAgJYQEAAi4uLY2q1mmtPSUlhY8eOZV5eXmzs2LEsJSWFa1u/fj3r06ePxnY8fPiw3njaVY9OqVTqOoQ2LSYmBpcvX+b+fHx8GrQ+YwxqtbqFotNe3759NbYjMDCQa3v//ffRp08fnDt3DgsWLMDcuXNRVFQEADh16hS++eYbfPfdd0hMTMSjR4+wfv16XW2GwdLmfZqVlQV3d/dmf+7MzEyIRCLY29s/t701PkN8fX2xcuVKODo6PtP2xRdfoLKyEomJidi1axf27duHPXv2aCyzadMmbt/dtm2bRlt9+3ZzKikpwauvvorExEQcP34cFhYW+Oijj7j2n3/+Gb///jv27duH/fv348SJE9i5cycAQKFQYPbs2YiKisKFCxcwZswYzJ49GwqFgls/IiJCYzvc3NzqjccgCt3evXvx2muvIS4uDv7+/ggNDcXJkye5dqlUio8++ghBQUHw9/fH7NmzAQDnzp3DoEGD8M0332DgwIFcoo8fP47Ro0dDIpEgOjoat27d4h7rm2++wdChQ+Hj44MRI0bgt99+49oePHiAyZMnw8/PD4GBgZg/fz7XlpaWhmnTpiEgIADh4eE4dOhQndvz+uuvY9euXVpt29NCQ0OxZcsWjBo1Cn379sWSJUtQUFCAmTNnwsfHB1OnTkVJSQm3fHJyMqKjoyGRSBAVFYVz585xbXv27EFERAR8fHwQFhbG7WhP5m7btm3o378/goKCnnlDaevSpUsYN24c/Pz8MG7cOFy6dEkjF2vXrkV0dDS8vb2xcOFCJCUlYdmyZfDx8cGyZcvw6NEj9OrVS+NDpiE5LCsrw5IlSxAUFITg4GCsXbsWKpWqwduRnp6OGzduYM6cOTA1NUV4eDh69uyJI0eOAADi4+Mxfvx4uLu7w8bGBrNnz653OC0pKYl7bUJCQrB3714u3kWLFqFfv34YMmQINm7cyH0B2Lt3L6Kjo/H5559DIpEgLCwMly5dwt69exESEoL+/ftrPOfixYsRExODadOmwcfHB5MnT0ZmZibXvmLFCoSEhMDX1xd/+9vfkJSUxLX9+9//xrx587Bo0SL4+Phg5MiRuHbtGgBgy5YtmDNnjsb2LF++HP/85z+fu62hoaHYvHkzRowYAX9/f3z00UeQy+UA6n6f/vLLL3jllVcQEBCAWbNmITc3FwAwdOhQZGRkYNasWfDx8YFCoeD2h7S0NMTGxiI5ORk+Pj6QSCQAgJMnT2LEiBHw8fFBcHAwtm7d+kyMf/75J6ZPn468vDz4+Phg8eLF3L63a9cuDB48GG+88QYA4NixYxg5ciQkEglef/11pKWlaWxrQ96jTxIKhZg6dSokEgn4/Gc/nhMTEzFz5kyYmZmhY8eOGD9+fKPfl/WZPHkyAMDf3x8+Pj64fPky1Go1Nm7ciCFDhqB///5YtGgRysrKnrt+SEgIIiIiYGlpCTMzM0yePFnjfR8fH4/p06ejQ4cOcHZ2xrRp07j99vz581AqlXjjjTcgFAoxZcoUMMZw9uzZxm9Qo/qlreDJocs9e/awPn36sJ9//pkplUq2Y8cONnDgQK6r++abb7J58+YxqVTKFAoFO3fuHGOMsbNnzzIPDw+2cuVKJpfLWWVlJbt+/Trr168fS05OZkqlku3du5cNGTKEG2I6dOgQy8nJYSqVih08eJB5e3tzXe4FCxawjRs3MpVKxaqqqtiFCxcYY4zJZDI2aNAgtnv3blZdXc2uX7/OAgICWGpq6nO37cmhuRdt2/PyMmHCBJafn89ycnJYv3792JgxY9iNGzeYXC5nr7/+Ovv3v//NGGMsJyeHBQQEsBMnTjCVSsVOnz7NAgICWGFhIWOMsePHj7MHDx4wtVrNzp07x7y8vNj169c1cvfll18yhULBTpw4wby8vJhUKn3hNj2puLiYSSQS9t///pdVV1ezhIQEJpFIWFFREbdeSEgIS01NZdXV1UyhUDzzWM8bRmlIDt955x326aefMplMxgoKCti4cePYTz/99Nzt2LNnD/P29mYBAQFs2LBh7KuvvuKe9+jRo2z48OEay3/22Wds2bJljDHGRo0axQ4ePMi1FRYWsp49e3Lb+qTMzEzWt29flpCQwBQKBSsqKuKGZxYuXMhmzZrFysrKWEZGBhs2bJjGtnp4eLDdu3czpVLJ1qxZw0JCQtjSpUuZXC5np06dYn379mXl5eWMMcY+/PBD1rdvX3b+/Hkml8vZ8uXLNYb14uPjWVFREauurmZbt25lAwYMYFVVVYyxmiEiT09PduLECaZUKtnq1avZhAkTGGOM5ebmMm9vb1ZSUsIYY6y6upr169ePXbt27bl5HTJkCBs5ciTLyspixcXFbOLEiWzNmjWMsee/T//8808WEBDArl+/zuRyOVu2bBmbNGmSxuM9OWz89P7w9NDlwIEDuferVCrl9vOnnT17lgUHB3O3H+97CxcuZDKZjFVWVrJ79+4xb29vdvr0aaZQKNg333zDhg4dyn2GNOQ9Wp/g4OBnhhYDAgLYlStXuNsbN25kEolEIy/9+/dngYGBbNq0aezmzZtcW3379tOe957btWsXGzp0KHv48CErLy9n7777Lvvggw9euB2M1QzpP953GGPM19eXJScnc7evXr3K+vbtyy07Y8YMjfXfeusttnXrVsZYzX7p6+vL/P392YgRI9iOHTte+PwG0aMDABcXF7z66qsQCAQYO3Ys8vPzUVBQgLy8PPzxxx/47LPPYGNjA2NjYwQEBHDr8fl8zJ07F0KhEKampvjll18wceJEeHt7c49lbGyM5ORkADVdYmdnZ/D5fIwYMQKdO3fG1atXAQBGRkbIyspCXl4eTExMuG+LJ06cgKurK8aNGwcjIyO89NJLCA8P577pN3bb6jJ58mQ4ODjA2dkZEokEXl5e6NOnD4RCIV555RWkpKQAAPbt24dBgwYhJCQEfD4fAwcOhKenJ9fbGTx4MDp16gQej4eAgAAMHDhQ4xu9kZER3n33XRgbGyMkJATm5uZIT0+vM64VK1ZAIpFAIpFg7NixXG46d+6MMWPGwMjICJGRkejWrRuOHz/OrTd27Fi4u7vDyMgIxsbGWuVM2xwWFBTgjz/+wJIlS2Bubg57e3tMnToVBw8efO7j+Pv7IyEhAX/99RfWr1+PgwcPct/+ZTIZrKysNJa3srKCTCYDAFRUVMDS0lKj7fF6T0tISMCAAQMQGRkJY2Nj2NrawsPDAyqVCocOHcL7778PS0tLdOzYEdOmTcP+/fu5dTt27Ihx48ZBIBBgxIgRyM7OxrvvvguhUIigoCAIhUI8fPiQW37w4MHw9/eHUCjEggULkJycjOzsbADA6NGjYWtrCyMjI0yfPh0KhULjNfbz80NISAgEAgFGjx7NjX44OTlBIpHg8OHDAGqGbW1tbeHp6Vnna/T3v/8dYrEYIpEI77zzjsZr8PT7NCEhAePGjcNLL70EoVCI9957D8nJyXj06FGdj18fIyMj3L17F+Xl5bCxscFLL73UoPXnzJkDc3NzmJqa4tChQwgJCcHAgQNhbGyMGTNmoKqqCpcvX+aW1/Y92lDBwcH45ptvUF5ejgcPHmDPnj2orKzk2letWsUNFwYGBmLGjBkoLS0FUP++rY2EhARMnToVbm5usLCwwHvvvYdDhw69cDj31q1b2LhxIxYtWsTd97z3SkVFBRhjz32fWVpacu+jiIgIHDp0CH/99ReWL1+OjRs34sCBA/XGYDCFzsHBgfvfzMwMQE2ycnJyYGNjAxsbm+euZ2trCxMTE+52VlYWtm/fzn0gSyQS5OTkIC8vD0BNl/rxsKZEIsGdO3dQXFwMAFi4cCEYYxg/fjxGjhyJ3bt3A6gZ17969arGYyYkJCA/P79J26bN8iYmJhq3TU1NuXWzsrJw+PBhjbguXrzIxXXy5Em8+uqrCAgIgEQiwR9//MFtKwCIRCIYGRlpxFZfXJ988gmSkpKQlJTEDUPk5eXBxcVFYzkXFxduGAoAxGJxnY+prbpymJWVBaVSiaCgIC4HMTEx3O9qT3Nzc4Obmxv4fD569eqFd999l/vCYmFhgfLyco3ly8vLYWFhAQAwNzfXaH/8/+P2J2VnZ6NTp07P3F9cXIzq6mqNnD2dryd/PzI1NX1m+01MTDSKa4cOHbj/LSwsYGNjw+3v27ZtQ0REBPz8/CCRSFBWVqaxDzy9b8nlcu6DbezYsVwB3r9/P0aPHv3M9jzpydfZxcWFiwF49n2al5cHV1dXjbhFIpFGHhpi/fr1OHnyJIYMGYLJkydrFCVtPJnDp/dpPp8PsVisEZu279GG+uSTT2BiYoLw8HDMnj0bI0eO1IjNz88PpqamMDMzw9tvvw0rKyvuy2t9+7Y2nn5NXF1doVQqUVhYWOc6Dx48wJtvvoklS5ZwHQOg5r3y5D5aXl4Oc3Nz8Hi8577PZDIZ9z7q0aMHnJ2dIRAI4OvriylTprxwO4zqbTUAHTp0QElJCUpLS2Ftbf1MO4/H07gtFosxa9YsvPPOO88sm5mZiU8++QTfffcdfHx8uG+xjzk6OmLFihUAan5fmTZtGvz9/SEWi+Hv74/t27c389Y1jVgsxujRo7mYn6RQKDB37lzExcUhLCwMxsbGmD17NlgzT2bh5OSErKwsjfuys7MRHBzM3X76NXqaubk5AKCqqor7Fqjtl4gOHTpAKBTi7NmzGkVbWzwej8tJjx49kJGRgfLyci6OW7duITIyEgDg7u6O27dvY8SIEVybg4MDbG1tn3lcsVjMjRQ8ydbWFsbGxsjKykKPHj0A1OTL2dm5wbE/lpOTw/0vk8lQUlICJycnJCUl4dtvv8V3330Hd3d38Pl8+Pv7a70PDB06FEuXLkVqaipOnDiBhQsX1rv8414kUPMlzMnJibv99D7g5OSk8VtiRUUFpFKpVnl43v7k5eWFr7/+GtXV1dixYwfmz59f72/h9T2mk5MTUlNTuduMsSa/RtoSiUT417/+xd1es2YNvLy86lz+yf23oW1Pe/o1ycrKgpGRUZ0H7mRmZmLatGmYPXs2xowZo9Hm7u6OW7ducbHfunWLO7ioR48e2LZtGxhjXBy3b9/GpEmT6tzOF+2zBtOjq4uTkxMGDRqEzz77DCUlJaiursaFCxfqXH7ChAnYuXMnrly5AsYYKioqcOLECZSXl6OyshI8Hg92dnYAag7WuHPnDrfur7/+yn1o2NjYgMfjgc/nY/Dgwbh//z7i4+NRXV2N6upqXL16VeMHal2IiorC8ePHcerUKahUKsjlcpw7dw45OTlQKBRQKBSws7ODkZERTp48iTNnzjR7DCEhIbh//z4SEhKgVCpx6NAh3L17F4MHD65zHQcHB2RkZHC37ezs4OzsjH379kGlUmH37t0a7fVxcnLCwIED8f/+3/9DeXk51Go1Hj58iPPnzz93+ZMnT3LDxmlpadi4cSPCwsIAAF27doWHhwc2bNgAuVyO3377Dbdv30Z4eDiAmmHA3bt34+7duygpKcHXX3/NDeE+bdSoUfjzzz+5oZ/i4mLcvHkTAoEAw4cPx9q1a1FeXo7MzExs374dUVFRWm1vXduUlJQEhUKBdevWwdvbG2KxGDKZDAKBAHZ2dlAqlfjqq6+e+SZdn8c9i/fffx8vv/zyMz33p/3f//0fcnJyIJVKuQNT6jJq1Cjs3bsXN2/ehEKh4D7QO3bs+MK47O3tkZubyx2lp1AosH//fpSVlcHY2BgWFhYQCARab+fTIiIicPLkSfz111+orq7Gtm3bIBQKG3yUcV0UCgV3oE51dTXkcjn3Qf7w4UMUFxdDpVLh5MmT+Pnnn7kv7VlZWbh48SK3/pYtW1BcXAxfX18A9e/bT7OzswOfz9d4n0VGRuI///kPMjIyIJPJsHbtWkRERDz3C2Rubi7eeOMNTJo0Ca+99toz7aNHj8b27duRm5uL3NxcbN++nXuvBAQEQCAQ4Pvvv4dCocCPP/4IAOjXrx8A4Pfff0dJSQkYY7h69Sp++OGHOrfjMYMvdACwcuVKGBkZISIiAgMGDMB//vOfOpd9+eWXsXz5cixbtgz+/v4YNmwYd7Rbjx49MH36dERHR2PAgAFITU3ldhIAuHbtGiZMmAAfHx+88847+Pjjj+Hm5gZLS0ts3boVhw4dQnBwMIKCgrB69WqNw2F1QSwWY+PGjdi8eTP69++PkJAQbN26FWq1GpaWlvjkk08wf/58+Pv748CBAwgNDW32GGxtbbFp0yZs374dgYGB2LJlCzZt2sR9mXiex0MR/v7+XG90+fLl2Lp1KwIDA3H37t0GfaisXLkS1dXV3BF/c+fOrbNHePbsWURFRaFv375466238Morr+Dtt9/m2tesWYPr16/D398fq1evxvr167ltGTRoEGbOnIkpU6ZgyJAhcHV1xdy5c5/7PC4uLvj222+xfft2BAQEYMyYMdzvX59++inMzMwwdOhQTJo0CZGRkRg3bpzW2/u0yMhIbNiwAYGBgbhx4wZWrVoFAAgKCsKgQYMQHh6O0NBQmJiYNHgYecyYMUhNTX3hsOXjOKZPn46hQ4fCzc3tuaMqj/Xv3x/z5s3DnDlzEBQUhIyMDKxdu1armPr164cePXogKCiIO3x+3759CA0Nha+vL3bu3ImVK1dqt4HP0a1bN6xatQrLly9Hv379cPz4cWzatAlCobDRj/mk4cOHw8vLC7m5uZgxYwa8vLy4ntT169cxatQo+Pr6Ys2aNVi9ejXXE5LJZFi6dCkCAgIwaNAgnDp1Ct9++y03ovCifftJZmZmmDVrFl577TVIJBIkJydj3LhxiIqKwuTJkxEWFgahUIhPP/30uevv2rULGRkZ2LBhA3x8fLi/x6KjozFkyBCMGjUKo0aNQkhICKKjowHUHHm6YcMG7Nu3DxKJBHv27MGGDRu4/B46dAjDhg2Dr68vFi1ahDfffLPOL5SP8Vhzj1URQvTG4sWL4ezsjAULFrTI42dlZSEiIgJnzpzROLjgaaGhoVixYgUGDBjQInEQUp820aMjhLQ+tVqN7du3Y8SIEfUWOUJ0zeAPRiGEtL6KigoMHDgQLi4u2LJli67DIaReNHRJCCGkTaOhS0IIIW0aFTpCCCFtGhU6QgghbRodjFKH4mIZ1Grd/Xxpb2+JwkLtT95tyygXtSgXtSgXtXSdiy93XYGDyBzzopvnpPnmRoWuDmo102mhexwDqUG5qEW5qEW5qKWrXBRIK5F8pwDTRnjo5Pm10SpDl3FxcQgNDUWvXr00rhEnl8sRGxuLYcOGYdSoURpn2aenp2PixIkIDw/HxIkTcf/+/Sa3EUIIaV6X79RcVuylrs9e01VftEqhCwsLw44dOzSufA3UTClhYmKCI0eOICEhAfPmzePaYmNjMWnSJBw5cgSTJk1CTExMk9sIIYQ0r0up+XB1tICDjZmuQ6lTqxQ6iUTyzDX0ZDIZ4uPjMW/ePO4K1Y+nsigsLERKSgp3VfjIyEikpKSgqKio0W2EEEKaV1mFAqmPpPBxd9R1KPXS2W90GRkZEIlE+Oqrr3Du3DlYWFhg3rx5kEgk3JQXj68wLhAI4OTkhOzsbDDGGtVW30WECSGENFzy3QIwBvj1pEL3XEqlEhkZGejTpw8+/PBDXLlyBbNmzcJvv/2mq5A02Nvr/tp9jo5WL16onaBc1KJc1KJc1NJFLlIeSOFoawY/T/EL55XUJZ0VOhcXFxgZGXHDjN7e3rC1tUV6ejo3o7JKpYJAIIBKpUJeXh7EYjEYY41qa6jCwnKdHtHl6GiF/PwynT2/PqFc1KJc1KJc1NJFLuQKFS7dzkOItwsKCsrB5/P0ooPwPDo7YdzOzg6BgYHcZJ/p6ekoLCxE586dYW9vDw8PDxw4cAAAcODAAXh4eMDOzq7RbYQQQprP9fRCVCvV8NHzYUuglS7qvGLFChw9ehQFBQWwtbWFSCTCwYMHkZGRgSVLlkAqlcLIyAjz589HSEgIgJoZcBcvXozS0lJYW1sjLi4O3bp1a1JbQ1CPTn9QLmpRLmpRLmrpIhffJtzA1bRCfDk3CAI+X697dDR7QR2o0OkPykUtykUtykWt1s6FUqXG/PWn4ePugBmRfQBArwsdXeuSEEJIg9zOkKJCroSvAQxbAlToCCGENNDl1HwIjfjo09Uwjn+gQkcIIURrasZw+U4BPLvZw8RYoOtwtEKFjhBCiNYe5JShuEwOH3cHXYeiNSp0hBBCtHYpNR98Hg/ePajQEUIIaYMupeajVycRLM2MdR2K1qjQEUII0Up2oQzZhRUGc7TlY1ToCCGEaOXx3HOG9PscQIWOEEKIli6l5qNLByvYWZvqOpQGoUJHCCHkhVIzpLiXVYoAD2ddh9JgVOgIIYTUizGG3SfSILIUYoivq67DaTAqdIQQQuqVfLcAdzNLEBXU1WBOEn8SFTpCCGlHGGO4dq8Qu47fRZVC+cLl1WqGvSfvwdnOHMFeDZ/bUx/obOJVQgghrUetZki6nYdDfz3Aw7xyAEBBSRVmjX6p3tnB/7yeg8wCGWaP8YSAb5h9Iyp0hBDShlUr1fjzejZ+PfcQecWV6GBnjmkjekNarsB//7iHbi7WCA/oVMe6KsSfvoeuYiv49TKsc+eeRIWOEELaqBPJmdh3Oh0l5Qp06WCFd8d6wsfdEXw+D4wxPMwpw67jaejSwQq9Otk+s37ipUwUlcoxY4RHvb0+fWeY/VBCCCH1yiuuwPeHb8PRxgzvR/fFp29I4NfLCXx+TcHi8XiYPtIDTrZm+Dr+OorL5BrrV1QpceDP+3ipqx08uhjGdDx1oUJHCCFt0JW0QgDAzEgPvNTF7rk9MjMTI7z7t5chr1ZjY/w1KFVqru3w+QeQVSkxPqR7q8XcUlqt0MXFxSE0NBS9evVCamrqM+1fffXVM23JycmIiopCeHg4pk+fjsLCwia3EUJIe3A1rRBie3M42ZrXu5yrgwWmj/RAWmYpdh67AwCQlstx9EIGAjyc0LmDVWuE26JardCFhYVhx44dcHV99mTDGzduIDk5GS4uLtx9jDEsXLgQMTExOHLkCCQSCVavXt2kNkIIaQ+qFErcflgMr+72Wi3v39sJ4QFuSLyUiT+vZyPhzH2oVAxjB3Vr4UhbR6sVOolEArH42XMwFAoFli1bhtjYWI2u9bVr12BiYgKJRAIAiI6OxuHDh5vURggh7UHK/WIoVQze3bW/+PL4wd3Ru5MI3x++jT+uZGGQtwucX9AbNBQ6/41u3bp1iIqKgpubm8b92dnZGj08Ozs7qNVqSKXSRrcRQkh7cOVuAcxMjNCjo43W6wj4fLw92hMWZsYQCHiIGtil5QJsZTo9veDy5cu4du0aPvjgA12G8Vz29pa6DgGOjoY/Nt5cKBe1KBe1KBe1HudCrWa4cb8Ifr2dIO6gfaGreQxg9dxBKJUp0MNN1BJh6oROC92FCxdw7949hIWFAQBycnIwY8YMfPHFFxCLxcjKyuKWLSoqAo/Hg0gkanRbQxQWlkOtZk3cwsZzdLRCfn6Zzp5fn1AualEualEuaj2Zi/s5pSgqlaNXR5tG5YcHwMZU0OB1+XyeXnQQnkenQ5dvvfUWTp8+jcTERCQmJqJDhw7YunUrgoKC4OnpiaqqKiQlJQEAdu7ciYiICABodBshhLR1V+8WggfgZS0PRGkPWq1Ht2LFChw9ehQFBQWYNm0aRCIRDh48WOfyfD4fK1euRGxsLORyOVxdXbFq1aomtRFCSFt3Ja0A3VysYW0u1HUoeoPHGNPd+Jweo6FL/UG5qEW5qEW5qPU4FyUyBRb8+zTGDuqGUQO6tGoMNHRJCCGkxV1NKwAAeNOwpQYqdIQQ0kZcTSuErZUJ3Jz0s2elK1ToCCGkDVCq1LiRXgSv7vYGPdNAS6BCRwghbUBqhhRVClWDrobSXlChI4SQNuDK3UIYCfjw6PzsvHLtHRU6QghpA66mFcCjsy1MhAJdh6J3qNARQoiBy8wvR25xpdazFbQ3VOgIIcTAXUjJBUCnFdSFCh0hhBi4Cyk5cHWwgIPITNeh6CUqdIQQYsAq5UrcuFcIrx7Um6sLFTpCCDFgN9KLoFI3bJLV9oYKHSGEGLArdwtgaWaM7q7Wug5Fb1GhI4QQA1VRVY0Lt/PQ/2UxBHz6OK8LZYYQQgzUmWs5UFSrMWJgV12Hoteo0BFCiAFSM4bES4/Q3dUaPTqKdB2OXqNCRwghBiglvQi5xZUI8+2o61D0HhU6QggxQImXMmFtIYSkt5OuQ9F7VOgIIcTA5EsrceVuAQZ5u8BIQB/jL9JqGYqLi0NoaCh69eqF1NRUAEBxcTHefPNNhIeHY9SoUYiA8jkAACAASURBVPjHP/6BoqIibp3k5GRERUUhPDwc06dPR2FhYZPbCCHE0B2/nAkej4fBfV10HYpB0KrQVVdXIykpCT/++CM2btyIH3/8EUlJSaiurtb6icLCwrBjxw64urpy9/F4PMycORNHjhxBQkIC3NzcsHr1agAAYwwLFy5ETEwMjhw5AolE0uQ2QggxdIpqFU5dyYJvTwfYWZvqOhyDUG+hKyoqQlxcHIKDg/Hxxx/jzJkzuHfvHs6cOYOPP/4YwcHBiIuL0+iF1UUikUAsFmvcJxKJEBgYyN3u27cvsrKyAADXrl2DiYkJJBIJACA6OhqHDx9uUhshhBi6czdzIatSIpQOQtGaUX2Nf//73zF+/Hjs27cPzs7Oz7Tn5uYiISEBkydPxqFDh5oUiFqtxk8//YTQ0FAAQHZ2NlxcarvldnZ2UKvVkEqljW4TibQ/BNfe3rJJ29McHB2tdB2C3qBc1KJc1GpvuWCM4eSVbHTqYIUgPzfweDyurb3loiHqLXT79u2DUCiss93Z2RkzZ87ElClTmhzI8uXLYW5ujsmTJzf5sZpDYWE51Gqms+d3dLRCfn6Zzp5fn1AualEuarXHXNzNLMG9zBK8Ht4LBQXl3P36kAs+n6cXHYTnqbfQ1VfkMjIywOfz4erqWu9y2oiLi8ODBw+wadMm8P93GRuxWMwNYwI1w6g8Hg8ikajRbYQQYsgSLz2CmYkA/V96doSN1E3roy7fe+89XLp0CQCwZ88ejBw5EiNHjsSuXbuaFMDatWtx/fp1bNiwQaNgenp6oqqqCklJSQCAnTt3IiIioklthBBiqEpkCly4mYeBnmKYCuvto5Cn8BhjWo3P9e/fHydPnoRQKMSoUaOwdOlSWFtb491338XRo0dfuP6KFStw9OhRFBQUwNbWFiKRCF9++SUiIyPRpUsXmJrWHD3UsWNHbNiwAQBw6dIlxMbGQi6Xw9XVFatWrYKDg0OT2rRFQ5f6g3JRi3JRq73lIuFMOv57Kh3/fDMQYnsLjTZ9yIU+D11qXegkEgmSkpKQm5uL8ePH49SpUwAAX19frqfXllCh0x+Ui1qUi1rtKRcqtRqLvv4LLg4WeH9i32fa9SEX+lzotO7/enh4YPPmzcjMzMTgwYMB1Bx1aWmpnxtGCCFtReLFTBSXyTF5WE9dh2KQtP6N7p///CdSU1Mhl8sxf/58AMDly5cxatSoFguOEELaM8YY4k/dw0/H7sCzqx3NIt5IWg9dtjc0dKk/KBe1KBe12noulCo1vj98G6evZSPoZTGmDO9V53Ut9SEXbWLoEgBOnz6NmzdvoqKiQuP+efPmNWtQhBDSnlXKldgYfx030oswOqgrogZ20Tg5nDSM1oVu2bJl+PXXXxEYGAgzM7OWjIkQQtqt4jI5vtx1BZn5MkyL6I1gb7pwc1NpXegOHjyI+Pj4Z65XSQghpHlk5pdj7a4rkFUpMX+CFzy72es6pDZB60InEolgZUXXUiOEkJZQVFqFL368BGNjPhZP8kXnDvR521y0LnTTpk3DBx98gLfffvuZk6/d3NyaPTBCCGlP9py8B4VSjU+nSuBsa67rcNoUrQvd0qVLAQAnTpzQuJ/H4+HmzZvNGRMhhLQr6dml+OtGDkb060xFrgVoXehu3brVknEQQki7xBjDz4l3YWVujJH9O+s6nDZJ6xPGH8vKysLly5eRnZ3dEvEQQki7cvlOAVIzpBgT1BVmJnSx5pagdVbz8vLw3nvvITk5GSKRCFKpFN7e3lizZs1zJ2UlhBBSP6VKjV3H70Jsb45Bfek0gpaidY9u6dKl6N27N86fP4/Tp0/j/Pnz8PDwQGxsbEvGRwghbdbxy5nILa7Eq0N6QMBv8AAb0ZLWPbqLFy9i3bp1MDY2BgCYm5tj0aJFCA4ObrHgCCGkrZJVVWP/6XR4dLaFV3c6X64laf0VwsbGBmlpaRr33bt3D9bW1s0eFCGEtHUH/ryPiiolJob2oMt7tTCte3QzZ87E1KlTMX78eLi4uCArKwt79+6l61wSQkgD5RVX4NjFRxjoJUYnZzoxvKVpXeheffVVuLm54cCBA7h9+zacnJzwr3/9C/3792/J+AghpM3ZfSINfD4PY4O76TqUdqFBx7L279+/UYUtLi4OR44cQWZmJhISEtCzZ83kgenp6Vi8eDGkUilEIhHi4uLQpUuXFmsjhBBdu/NIiqTb+Rgd1BW2Via6DqddqLfQff3113jnnXcAAOvWratzuRcNX4aFhWHKlCn4+9//rnF/bGwsJk2ahNGjR2Pfvn2IiYnB999/32JthBCiSyq1Gj/9fgciSyGGB3TSdTjtRr0Ho+Tk5Gj8X9ffi0gkkmdmPSgsLERKSgoiIyMBAJGRkUhJSUFRUVGLtBFCiK4dOvsQ93PKEB3mDhOhQNfhtBv19ug+++wz7v8vvviiWZ84Ozsbzs7OEAhqXmyBQAAnJydkZ2eDMdbsbXZ2ds0aPyGENMTD3DLsP52OAA8nBHjQRTZaU72FLiMjQ6sHaYuzF+jDlPCOjnQ01mOUi1qUi1qGkotqpQrL/pMEawsh5r3mB2sLYbM/h6HkQhfqLXSvvPIKeDweGGN1LtPY2QvEYjFyc3OhUqkgEAigUqmQl5cHsVgMxliztzVUYWE51Oq6t7ulOTpaIT+/TGfPr08oF7UoF7UMKRe7T6ThfnYp5o33grxCjvwKebM+vj7kgs/n6UUH4XnqLXQtOWOBvb09PDw8cODAAYwePRoHDhyAh4cHN8TYEm2EENLa7maW4NdzDxDsJYZ3D4cXr0CaHY/V111rJitWrMDRo0dRUFAAW1tbiEQiHDx4EGlpaVi8eDFKS0thbW2NuLg4dOtWc15JS7Q1BPXo9AflohblopYh5EJercLSbeehVKmxbEZgi81OoA+50OceXb2FbtKkSVpdmmbHjh3NGpQ+oEKnPygXtSgXtQwhFzt+S8Wxi4+w8DUfeHS2bbHn0Ydc6HOhq/frxYQJE1orDkIIaVNu3i/CsYuPMNSvY4sWOfJi9Ra6sWPHtlYchBDSZlRUKbHt0E0425lj3ODuug6n3au30MXHx2PMmDEAgN27d9e53Pjx45s3KkIIMWB7TqahqEyOJZP9YGJMJ4brWr2F7uDBg1yh27dv33OX4fF4VOgIIeR/HuSU4cTlTIT6dUR3Vxtdh0PwgkL37bffcv//8MMPLR4MIYQYMsYYdvyeCktzY4wN7qrrcMj/NPhY1/LycshkMo37nJ3pcjaEEHL2Ri7uPirB1IjeMDc11nU45H+0LnRnzpxBTEwMMjMzNe5v7JVRCCGkLamUK/HL8bvoKrZCkFfDr8ZEWo7Whe6TTz7B7NmzMWLECJiamrZkTIQQYnASztxHiUyBOeO8wNfi/GPSerQudHK5HH/729+4mQEIIYTUyCqQ4bekDAR7idHNxVrX4ZCn1Dsf3ZOmTp2KLVu21HuBZ0IIaW8YY/jp91QIjQUYF0LnzOkjrXt0w4YNw4wZM7B582bY2mqe5X/s2LFmD4wQQgzBpdQC3LhfjElD3Vtk+h3SdFoXurlz50IikWD48OH0Gx0hhKDmos07j91BR0cLDPF11XU4pA5aF7pHjx4hPj4efL7Wo52EENKm/Xr2AQpLq/DhJB8I6LNRb2n9yoSFheHs2bMtGQshhBgMabkch84+RICHE3p1oos26zOte3QKhQLvvPMOJBIJ7O3tNdpWrlzZ7IERQog+u59TBqVKjaESN12HQl5A60Ln7u4Od3f3loyFEEIMRr60EgDgZGum40jIi2hd6P7xj3+0ZByEEGJQ8qWVMBEKYGVGl/rSd/X+Rnfr1i2tHkTb5QghpK0okFbB0cYMPLoKit6rt0f32WefwdLSEqNHj4a/v7/GxZvz8vJw4cIFxMfHo6KiAjt27Gh0EMePH8e6devAGINarcacOXMwbNgwpKenY/HixZBKpRCJRIiLi0OXLl0AoNFthBDSHPKklehgZ67rMIgWeOwFlzo5fvw4du7cibNnz4LP58PCwoKbvaB///6YOHEiQkJCGh0AYwwBAQHYsWMHevbsiVu3buG1117DxYsXMXXqVIwbNw6jR4/Gvn37sGfPHnz//fcAgClTpjSqTVuFheVQq3V3FRhHRyvk55fp7Pn1CeWiFuWili5zwRjDrH+dRKivKyaG6v7YBX3YL/h8HuztLXUaQ11e+BvdkCFDMGTIEFRXV+PBgwcoLS2FjY0NOnfuDCOjBs/y81x8Ph9lZTUvUllZGZycnFBcXIyUlBRs374dABAZGYnly5ejqKgIjLFGtdnZ2TVLvISQ9q1EpkC1Ug1HER2IYgi0rlTGxsbo0aMH1Go1CgoKmq3I8Xg8fPnll5g9ezbMzc0hk8mwefNmZGdnw9nZmbuItEAggJOTE7Kzs8EYa1QbFTpCSHN4fMQlFTrDoHW1KikpwbJly3DkyBEYGRkhOTkZx44dw9WrV7FgwYJGB6BUKrF582Zs3LgRfn5+uHjxIhYsWKDzc/P0oQvu6Gil6xD0BuWiFuWilq5yce2BFADQq5sDHB11/1kB0H5RH60L3dKlS2FtbY3ExESMHDkSAODj44O4uLgmFbqbN28iLy8Pfn5+AAA/Pz+YmZnBxMQEubm5UKlUEAgEUKlUyMvLg1gsBmOsUW0NQb/R6Q/KRS3KRS1d5uJeRjF4AHhKlV68HvqwX+jzb3RaXwLsr7/+wieffAInJyfucFo7OzsUFhY2KYAOHTogJycH9+7dAwCkpaWhoKAAnTt3hoeHBw4cOAAAOHDgADw8PGBnZwd7e/tGtRFCSHPIl1bC1toExkZ0fUtDoHWPzsrKCsXFxXBycuLuy8rKgqOjY5MCcHR0xNKlSzFv3jyugH7xxRcQiURYunQpFi9ejI0bN8La2hpxcXHceo1tI4SQpsqXVsLRhn6fMxRaF7oJEyZg7ty5mD9/PtRqNS5fvow1a9YgOjq6yUFERUUhKirqmfu7d++OXbt2PXedxrYRQkhT5Usr4dnN/sULEr2gdaF78803IRQKsWzZMiiVSixZsgQTJ07EG2+80ZLxEUKIXlFUqyAtV9ARlwZE60LH4/EwdepUTJ06tQXDIYQQ/ZZfUgUAcBTRBNSGQutC99dff9XZ1r9//2YJhhBC9B2dQ2d4tC50H3/8scbt4uJiVFdXw9nZGceOHWv2wAghRB9RoTM8Whe6xMREjdsqlQpff/01LCwsmj0oQgjRVzQ9j+Fp9EkgAoEAs2bNwpYtW5ozHkII0Ws0PY/hadLZjmfOnKEXmxDSruRLK+lAFAOj9dBlSEiIRlGrrKyEQqFAbGxsiwRGCCH6hjH2v3Po6EpLhkTrQrdq1SqN22ZmZujatSssLfXz2maEENLcSmQKKGh6HoOjdaELCAhoyTgIIUTv0RGXhknrQieVSrFt2zbcvHkTFRUVGm07duxo9sAIIUTfUKEzTFoXuvfffx8KhQIREREwM6MXmRDS/uRLq8ADYG9NB6MYEq0L3eXLl3H27FkIhcKWjIcQQvQWTc9jmLR+tXr16oWcnJyWjIUQQvQaTc9jmLTu0fXr1w8zZ87E3/72Nzg4OGi0jR8/vtkDI4QQfZMvrYRnV5qex9BoXeiSkpLg7OyMM2fOaNzP4/Go0BFC2jxueh5b6tEZGq0L3Q8//NCScRBCiF6j6XkMV4N+US0uLkZ8fDx3fcvc3Fz63Y4Q0i7QqQWGS+tCd/78eQwfPhwJCQnYsGEDAODBgwdYunRpk4OQy+WIjY3FsGHDMGrUKHz66acAgPT0dEycOBHh4eGYOHEi7t+/z63T2DZCCGkMKnSGS+tC9/nnn+PLL7/E1q1bYWRUM+Lp7e2Nq1evNjmIVatWwcTEBEeOHEFCQgLmzZsHAIiNjcWkSZNw5MgRTJo0CTExMdw6jW0jhJDGoOl5DJfWhS4zM5ObSfzxxZ2NjY2hUqmaFIBMJkN8fDzmzZvHPa6DgwMKCwuRkpKCyMhIAEBkZCRSUlJQVFTU6DZCCGksmp7HcGl9MEr37t1x6tQpBAcHc/f9+eef6NmzZ5MCyMjIgEgkwldffYVz587BwsIC8+bNg6mpKZydnSEQCADUzH/n5OSE7OxsMMYa1WZnR1ccJ4Q0Tr60Ek50xKVB0rrQLV68GG+//TYGDx6MqqoqxMTEIDExERs3bmxSAEqlEhkZGejTpw8+/PBDXLlyBbNmzcK6deua9LhNZW+v+1kZHB2tdB2C3qBc1KJc1GqtXDDGkF9SBf+XOuht/vU1Ln2gdaHr27cv9u/fj/3792PcuHEQi8XYvXs3OnTo0KQAXFxcYGRkxA01ent7w9bWFqampsjNzYVKpYJAIIBKpUJeXh7EYjEYY41qa4jCwnKo1axJ29YUjo5WyM8v09nz6xPKRS3KRa3WzEVJuRyKahUsTQR6mX992C/4fJ5edBCeR+vf6G7evAlnZ2e8+eabiI2NxVtvvdXkIgcAdnZ2CAwM5E5ET09PR2FhIbp06QIPDw8cOHAAAHDgwAF4eHjAzs4O9vb2jWojhJDGyKMjLg0ajzGmVbelX79+sLOzQ2RkJEaNGgU3N7dmCyIjIwNLliyBVCqFkZER5s+fj5CQEKSlpWHx4sUoLS2FtbU14uLi0K1bNwBodJu2qEenPygXtSgXtVozF39ez8aWAzfx+Vv90MHOvFWesyH0Yb/Q5x6d1oVOpVLh1KlTOHDgABITE+Hu7o7IyEiMGDEC9vZt79pvVOj0B+WiFuWiVmvmYt/pdOw/nY5NHwzWy5kL9GG/0OdCp/VvdAKBAIMHD+YORjl27Bh++uknxMXF4fr16y0ZIyGE6BRNz2PYGvyqyeVyHD9+HIcOHcL169chkUhaIi5CCNEbND2PYdO6R3fy5EkkJCQgMTERPXr0wIgRI7B06VI4Ojq2ZHyEEKJzND2PYdO60MXFxWHkyJGIj49Hp06dWjImQgjRG9z0PDRrgcHSutAdOnSoJeMghBC9VPB4eh66KorB0vo3OoVCgbVr1yIsLAx+fn4AgNOnT+PHH39sseAIIUTX6Bw6w6d1ofvnP/+J1NRUrF69mruoqbu7O3766acWC44QQnSNpucxfFoPXR47dgxHjx6Fubk5+Pya+ujs7Izc3NwWC44QQnSNpucxfFr36J43JU9RURFEIlGzB0UIIfqCpucxfFr36IYPH44PP/wQH330EQAgLy8Pn3/+OUaOHNliwRFCSEuTV6twKTUfD3PLoFYDasbAGIOa1cxacDezBO4dbXQdJmkCrQvdggULsGrVKkRFRaGyshLh4eGYMGEC3n333ZaMjxBCGqS0QgEjPh/mpnV/vDHGkJZZitPXsnHhVi4q5SoYG/FhJOCBz+OBx+OBz6uZZNrYiI++PRxacQtIc9P6WpdPKioqgq2tLW7fvo2NGzdi/fr1LRGbTtG1LvUH5aIW5aLW07moqFJi/5l0HLv4CCo1g62VCVwdLdDRwRKujhZwdbSAuakxLtzMxelrOcgtqoDQmA//Xk4Y+LIYPTuJwDfQ4Ul92C8M+lqXlZWV2Lx5M27duoXOnTtjzpw5kMlkiImJwZkzZzBmzJjWiJMQQp5LzRhOX83GnpNpKK+oRrC3C5xszZCZX47MfBl+f/AISpVaY51ebiKM7NcZfr0cYWai9cAWMVAvfIWXLVuGlJQUBAUF4Y8//kBqairu3buHMWPGYNmyZTTPGyFEZ+5mluD/fkvF/ZwyuHe0waRXe6JzB82ZtlVqNfKKK5FVIIO0XIGXu9nByVb/ptohLeeFhe7UqVPYt28f7O3t8frrr2Pw4MH44Ycf4O/v3xrxEULIM4rL5Pjht1Qcv/gItlYmeCuqDwI9nJ97ZKSAz4fY3gJiewsdREr0wQsLXUVFBTffXIcOHWBubk5FjhCiE2UVCvx69iGOXXoExoCR/TtjZP/OMBXS8COp2wv3DpVKhbNnz+LJY1aevt2/f/+WiY4QQlBzoMmR8w9xNCkDimoV+r/UAdOiPCFQq1+8Mmn3XnjUZWhoaP0PwOPh2LFjzRqUPqCjLvUH5aJWe8uFXKHC7xczcPjcQ8iqlJD0dsKYoK5wcbBod7mojz7kwqCPukxMTGyNOAAAX331Ff79738jISEBPXv2RHJyMmJiYiCXy+Hq6opVq1Zxw6iNbSOEGIZzKbn46fdUlFZUw6u7PcYGd3vmQBNCtKE388LfuHEDycnJcHFxAVBzQufChQsRExODI0eOQCKRYPXq1U1qI4Tov0q5Et8mpGDz/htwEJlhyet+mD/Bm4ocaTS9KHQKhQLLli1DbGwsd9TUtWvXYGJiAolEAgCIjo7G4cOHm9RGCNFvdx5JEbvtPM6m5GB0UFd8NNkXPVzp8lukafTiUKV169YhKioKbm5u3H3Z2dlc7w4A7OzsoFarIZVKG93WkAtQ68NYs6MjfYN9jHJRqy3mQqlSY+dvt7Hr91Q42ppj5T+C0bvLi8/RbYu5aCzKRd10XuguX76Ma9eu4YMPPtB1KBroYBT9Qbmo1RZzkVtcgW8TUnAvqxQDPTtg0is9YWZi9MLtbIu5aCx9yIVBH4zS0i5cuIB79+4hLCwMAJCTk4MZM2bg9ddfR1ZWFrdcUVEReDweRCIRxGJxo9oIIfpDrlDhyPmHOHTuAYz4fMwa/RICPJx1HRZpg3Re6N566y289dZb3O3Q0FBs2rQJPXr0wC+//IKkpCRIJBLs3LkTERERAABPT09UVVU1uI0Q0jJKZQrcSC9CUVkVvLo7oKOjRZ3zt6kZw1/Xc7DnZBqk5Qr49XLEa2HusLM2beWoSXuh80JXFz6fj5UrVyI2NlbjNIGmtBFCmodKrUZaZimupxfi2r0iPMipHTbbc/IexPbm8O/thAAPZ7g41F566+aDYvyceAcPc8vRVWyFWaM90dONRltIy2rUND3tAf1Gpz8oF7UamovUDCmSbuXBo4stvLrbQ8Bv/IHWFVVKXEkrwOXUfNy4X4xKuRJ8Hg89XK3h2c0eL3ezh8jKBJdS83HhZi5uP5SCAXB1tIB/byc8yCnD5TsFsLc2wbiQ7gjo49ykaXFov6ilD7mg3+gIIa0qLbME8afu4cb9YvB4wO//u/jxIG8XDPJ2ga2ViVaPU1qhQPKdAly8nY+U+0VQqRlsLIXw7+0Iz6726NPF7pkJTof4uGKIjyuk5XJcvJ2P8zdzEX8qHSZCAcaFdMMrEjcIjQUtsdmEPBcVOkLakPs5pYg/lY6raYWwNDPGq0N6IKSvC1LuF+NEcib2nU5Hwpn78O5hj5C+rvDsaocqhQplFQqUVVSjrEKB0goFSmUK3HxQjNsZUjAGONiY4hWJG3x7OaKbi7VWPTGRpQnC/DoizK8jSsrlMDbiw9zUuBWyQIgmKnSEtAGP8svx3z/u4fKdAliYGmFcSDeE+XXkrurv18sRfr0ckSetxB/JWTh1NQuX7xSAxwPq+vFCbG+Okf27wK+nIzo5W9Z5cIk2bCy160ES0hKo0BFi4E5dycL3R25DaMzHmKCueMXfrc5Zs51EZhg/uDvGBHfFpdR8ZOSVw9LMGFbmxrA2F8LKXAgr85rbxkY0vEjaBip0hBgotZrhl+N3cfRCBl7qYou3R3vC0ky7oUEjAR8BHs503hppF6jQEWKAKqqU2LT/Oq7fK8JQv46YGNajSUdUEtKWUaEjxMDkFldg/e6ryCuuxJThvTC4r6uuQyJEr1GhI8SAXL2bj8//kwQAeH9iX/TubKvjiAjRf1ToCDEQJ5Mz8ePRVDjbmWPuuJfhZGuu65AIMQhU6AjRc4wx7D9zH/tOp8O3txNmRPSu86hKQsiz6N1CiB5Tqxl+PHobJ5KzMNCzAz6Y4o/iIpmuwyLEoFChI0RPVStV2Lw/BZdS8zGiX2eMC+kGIwEdWUlIQ1GhI0QPVVRVY/3uq0h9VILXwtzxir+brkMixGBRoSNEzxSXybHml2TkFFbg7aiXENiHTuompCmo0BGiR24+KMa2gymQVSmx4FVv9Olip+uQCDF4VOgI0QP3c0qx50Qabtwvhp21CT6c5IvOHax0HRYhbQIVOkJ0KLtQhv+eSkfSrTxYmhljYmgPhPq60gWVCWlGVOgI0YGi0irsP5OO01dzYGzER9TALggP6ETnxxHSAnT+riouLsaiRYvw8OFDCIVCdO7cGcuWLYOdnR2Sk5MRExMDuVwOV1dXrFq1Cvb29gDQ6DZCdCmvuAK/nnuIM9eywRgQ6uuKyAFdYG0h1HVohLRZOj8ph8fjYebMmThy5AgSEhLg5uaG1atXgzGGhQsXIiYmBkeOHIFEIsHq1asBoNFthOhKRl45Nu+/gY++OYsz17Ix8GUxvnirHya90pOKHCEtTOeFTiQSITAwkLvdt29fZGVl4dq1azAxMYFEIgEAREdH4/DhwwDQ6DZCWtvdRyVYt+sKYredR/LdAoT7d0LcrAF4Y3hvOIjMdB0eIe2Czocun6RWq/HTTz8hNDQU2dnZcHFx4drs7OygVqshlUob3SYSibSOxd7esnk2qgkcHemou8cMKRdKlRp/XcvGgdP3kJJeBCtzIf4+vDdGDuwKK/Om994MKRctjXJRi3JRN70qdMuXL4e5uTkmT56M3377TaexFBaWQ61mOnt+R0cr5OeX6ez59Ymh5KJUpsDJ5EycSM5CcZkcjiJTRIe5I8TbBSZCAapkclTJ5E16DkPJRWugXNTSh1zw+Ty96CA8j94Uuri4ODx48ACbNm0Cn8+HWCxGVlYW115UVAQejweRSNToNkKaG2MM93PK8HvSI1y4lQuliuGlrnZ4PbwXvLrZg8/n6TpEQto9vSh0a9euxfXr1/HNN99AKKwZ2vH09ERVVRWSkpIgkUiwc+dORERENKmNkMbKk1Yiq0CGfGkl8qWVKJBW1fxfUglFtRomQgEGebsgzK8jxPYWug6XEPIEHmNMd+NzAO7cuYPILS8BrwAACnlJREFUyEh06dIFpqamAICOHTtiw4YNuHTpEmJjYzVOE3BwcACARrdpi4Yu9Ycuc1GlUGLXiTQcv5TJ3WdiLICjyBSOIjM42JjB1dEC/r2dWuUcONovalEuaulDLvR56FLnhU5fUaHTH7rKRcr9Inz36y0UllQhTNIRgR7OcBSZwcrcGDyeboYkab+oRbmopQ+50OdCpxdDl4Tok0q5EruO38WJ5Cw425ph8WRfuHek33gJMVRU6Ah5wvX0Qnz36y0Ul8kxPKATxgR3hdCYrjtJiCGjQkcIgIe5ZTh8/iHO3siF2N4cSyb7oburja7DIoQ0Ayp0pN1SM4ardwvxW1IGbj4ohtCYjxH9OmN0UBeaPYCQNoQKHWl35AoVTl/Lxu9JGcgtroStlQkmDO6OYG8XWJoZ6zo8Qkgzo0JH2jylSo2HueVIyypBelYprqYVokKuRFexNd6O6ga/Xo4wEuj8sq+EkBZChY60KUqVGjlFFXiUX470rDLcyyrBg9wyKFU1p4rYWpnAq7s9Qn07orurtc5OEyCEtB4qdMTgVCvVKKtQoKyiGrnFFcgqkCGzQIasAhnyiiuh+t/5j0IjPrp0sMJQPzd0c7FGNxdr2Fmb6jh6Qkhro0JH9ApjDNJyBbILZcgurEBOYQVKq6pRKK3kiluVQqWxDo8HOInM4OJgAd+ejnB1sIDL//5oSJIQQoWO6ExZhQIP88qRkVuOR/nlXHF7spCZCgUQO1jAXCiAk8gGlubGsDIXwsrcGFZmQjiKTCG2N6ejJAkhdaJCR1qUoloFabkcxWU1f5kFMmTkleNhbhmk5QpuORtLIVzsLTDAswPE9hYQ25tDbG8BkaUQTk7WOr+8ESHEcFGhI01SpVAir7jmiv550krkFVeisLQK0v8VNlmVUmN5AZ8Hsb05PDrbwc3JEm7OlnBzsoR1M0xISgghz0OFjtSrWqlGUWkVCkqrUFhShYKSShSUVKGgpAp5xZUolSk0lrc0M4aDTc2V/d3dRLC1NIGtlQlEliYQWZnASWQGYyP63YwQ0nqo0LUjjDEolGpUVClRIVeioqoaFVVKlFdWo1SmQGmFAqWyapRWKFAmU6BEpkCpTIEn53Dg83iwszaBg40pvLvbw8nWDE625nASmcFRZAZzU9qlCCH6hT6V9JBazSCrrEaJTIFqpQrVSnXNn0oNpVINpYpBpWZQqdVQqRjUjEGlYv+/vbsLieJf4wD+3ZnZ13LbXSVTe78orCBhQ8FAUcSlcrOXC7tQAiGIiqirTAkJjbQgu8goouu6iaT0EAbVTRBp0oYgFWqxoam7Kv2t3XF25zkXW5OHc9o6Wi7NPB9Yxvk9zu78vjj74Owsg1hcxeevjWsmkrhCMfGzgs8RBV/kmPZ9sv/FIglwLrEgzWGBO82KNSvSkO60IX2ZDRnLEkt3mhWiwP+RMcb+HtzoflEsrmImoiAixxCdjSMqxxCZjSM6m1j/Nv5FjiVqcmIsMhuDKJhgNYuJh+X70iwKWmP658vs16WCz1EFC7lLoCiYElcn2s1YajcjJ2MJltrNcNjMcNgkOKxSYmmT4LCasdQuwbnEAqtZ5C9QM8Z0hxvdD/zr2XuMhD5rp/O+RJWfbiMKJlgtEqxmAXaLBJfTikyzAyoRFEWFrMQxE1Ew+Y+MWSUOJa7CbjVjqU1CxjIbVmemfW1IEjLcSzArK5AkEyRRgFkUIUkCJAEQRQGiYIIgmCAKQmJpSry+3WaG1SzormEJgr7msxCcxXecxXepziLVr58M32GcMcaYrvGHLYwxxnSNGx1jjDFd40bHGGNM17jRMcYY0zVudIwxxnSNGx1jjDFd40bHGGNM17jRMcYY0zVudIwxxnSNG90iaG1tRWlpKTZu3Ig3b95o40+ePMHevXvh9/tRXV2NYDCo1WRZRmNjI8rLy+H3+3HmzBmtNjw8jKqqKvh8PlRVVeHdu3eLOZ0F+X+z+PDhAyorK7VHaWkp8vPzte2MlAUAPH78GHv27EFlZSX8fj+6u7u1mtGySFb7m7OYmprCoUOH4PP54Pf7cezYMUxOTgIAXr58id27d8Pn86G2thbhcFjbbr41QyD2x/X09NDIyAiVlJTQ69eviYhoenqa8vPzaWhoiIiIOjo6qLa2VtumqamJzp07R6qqEhHRxMSEVqupqaGOjg5tu5qamsWayoLNJ4u5mpub6ezZs9q6kbJQVZW2bdum/e7AwADl5eVRPB4nImNl8bO/mb85i6mpKXr27Jm23tLSQqdPnyZVVamsrIx6enqIiKi9vZ3q6uqIiOZdMwpudIto7kEcCARo586dWm1qaoo2bNhA4XCYZmZmyOv10szMzH89RygUIq/XS7FYjIiIYrEYeb1eCofDizOJ3+RXs5hLlmUqKCig/v5+IjJeFqqqUn5+PvX29hIR0fPnz6m8vJyIjJdFsppesvjmwYMHdPDgQQoEArRr1y5tPBwOU15eHhHRvGtGwacuU2TdunUIhUJ49eoVAOD+/fsAgNHRUQSDQbhcLly5cgX79u1DTU0Nent7tXpmZiZEUQQAiKKI5cuXY3R0NDUT+Q2SZTHXo0ePkJmZic2bN2t1I2VhMplw+fJlHDlyBCUlJTh69ChaWlq0upGySFbTUxaqquLWrVsoLS3F6OgosrOztZrH44Gqqpienp53zSj4Nj0pkpaWhra2Npw/fx6yLKOoqAhOpxOSJEFRFASDQWzatAmnTp1CIBDA4cOH8fDhw1Tv9h+RLIu57ty5g/3796doLxdHsixisRiuX7+Oq1evwuv14sWLFzh58iS6urpSvdt/RLIsfnb86EVTUxMcDgeqq6t1e/wvBm50KVRYWIjCwkIAQCgUws2bN7Fq1SpEo1FIkoSKigoAwNatW+F2uzE8PIzs7GyMjY0hHo9DFEXE43GMj48jKysrlVNZsB9l8c3Y2Bh6enpw4cIFbSwrK8tQWQwMDGB8fBxerxcA4PV6YbfbMTg4iJycHENlkawWiUR0kUVrayvev3+Pa9euQRAEZGVlYWRkRKtPTk7CZDLB5XLNu2YUfOoyhSYmJgAkTk9cunQJBw4cgMPhgMfjQUFBAZ4+fQogcQVZOBzGmjVrkJ6ejtzcXHR2dgIAOjs7kZubC4/Hk7J5/A4/yuKbu3fvori4GG63WxszWhYrVqzAx48fMTQ0BAAYHBxEKBTC6tWrDZdFspoesmhra0N/fz/a29thsVgAAFu2bEE0GtU+xrh9+zZ27NixoJpR8I1XF0FzczO6u7sRCoXgdrvhcrnQ1dWFhoYG9PX1QVEUbN++HfX19bBarQCAYDCI+vp6TE9PQ5IknDhxAsXFxQASb3B1dXX49OkTnE4nWltbsX79+lRO8ZfNJwsA8Pl8aGhoQFFR0X88n9GyuHfvHm7cuKHdQf748eMoKysDYLwsktX+5izevn2LiooKrF27FjabDQCwcuVKtLe3o6+vD42NjZBlGTk5Obh48SIyMjIAYN41I+BGxxhjTNf41CVjjDFd40bHGGNM17jRMcYY0zVudIwxxnSNGx1jjDFd40bHGGNM17jRMcYY0zVudIwxxnTt36AbeDYDYSAcAAAAAElFTkSuQmCC\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "y2 = avgs.revenue\n",
    "fig, ax = plt.subplots()\n",
    "plot(x, y2, ax, 'Increase in mean Fortune 500 company profits from 1955 to 2005', 'Revenue(millions)')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAA9sAAAEUCAYAAAA7qCWUAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy8QZhcZAAAgAElEQVR4nOzde1xUZf4H8M+ZgeGmieAN0TQ3U9NQCPCGmni/oZUm60/L1Lyn3TRrW03TXLGyMtRtNbtspZlmomZraaZlpm2mlqRpIgmKXGXuM+c8vz+Is4wyMODADPB5v17uNjxnzjznmXPmOd/z3CQhhAARERERERERuY3G0xkgIiIiIiIiqm0YbBMRERERERG5GYNtIiIiIiIiIjdjsE1ERERERETkZgy2iYiIiIiIiNyMwTYRERERERGRmzHYriZTpkzBJ5984ulseK1t27bhr3/9a5Xse8KECdiyZUupaUIIPPPMM4iJicHo0aOr5POJPvjgA/To0QORkZHIy8tDZGQk0tPTb3q/ZrMZ06dPx9133405c+a4IadEtR/r47KxPibynFWrVqFr167o2bOnp7NCbuJVwXZ8fDy+/fZbT2ejSqxfvx733nuvp7NR65RVcbvihx9+wDfffIMDBw7g448/rtQ+2rVrh7S0tErn4WYsWLAAnTp1QmRkpPpPlmU1/fDhwxg8eDA6d+6MCRMm4NKlS2qa1WrFM888g6ioKPTs2RMbN270xCHUejabDf/4xz/w1ltv4ccff0TDhg3x448/omXLlgCKvsNVq1ZVat979uxBdnY2jhw5gtdff92d2XbJmTNnMHnyZHTt2hXt2rW7If3cuXN48MEHcffdd2PAgAHYu3evmvbHH3+gXbt2DuducnKyml7euV3SzQYHn3zyCe677z5ERUWhd+/eSEpKgt1uV9Pz8/Mxa9YsdOnSBX379kVKSorD+1NSUtC3b1906dIFM2fORH5+vpo2YcIE3HXXXeoxDBo0qNL5rE6sj6miWB+zPqabk5mZiY0bN2L37t345ptvqv3zrVYr5syZg/j4eLRr1w5HjhxxSL927RqefvppdO/eHd27d8fq1asd0uPj4xEREaGe/5MmTVLTtm3bhg4dOjhcH9fvv1jx/UHJergijh8/jocffhixsbHo1q0b5syZg6ysLDVdCIGVK1eia9eu6Nq1K5KSkiCEUNNPnz6N++67D507d8Z9992H06dPq2mrV69Gx44dHY6jvMYTrwq2q0JlvyiqGy5duoTw8HAEBgZW+L3ecm5NnjwZP/74o/pPq9UCAHJzczF79mzMnTsX33//PTp16oTHH39cfd/q1auRlpaG/fv3491338X69evx9ddfe+owaqzyzoOcnBxYLBbcfvvtbv/sjIwMtG7dGj4+PpXK283y8fHB4MGDsWzZslI/e+bMmejbty++//57LFmyBPPmzcPvv//usN3Ro0fVc3fWrFkOac7ObXczmUx49tln8d1332HLli347rvv8NZbb6npS5Ysga+vL7755husXLkSzz//PM6ePQsAOHv2LBYuXIikpCR88803CAgIwOLFix32v3DhQvUYPv/88yo5hprAW34zyTuxPmZ9XB5v+Z6ryqVLlxAcHIzQ0NBS06vj+KOiopCUlITGjRvfkLZ8+XKYTCbs27cPW7ZswaeffoqtW7c6bLNu3Tr1/C9ZjwJAly5dHK6Prl27VskxFBQU4IEHHsC+ffuwf/9+BAUF4ZlnnlHTN2/ejC+++AKffvopduzYga+++gqbNm0CUPTAYebMmUhISMDRo0cxatQozJw5E1arVX3/kCFDHI6juPHEGa8NtotbKlasWIGYmBjEx8fjwIEDanp+fj6eeeYZxMXFISYmBjNnzgQAHDlyBL1798abb76Jnj17qoW7f/9+jBw5EtHR0UhMTERqaqq6rzfffBP9+/dHZGQkhg4d6tD6kpaWhvHjx+Puu+9G165d8dhjj6lp586dU5+cDBo0CLt373Z6PCWf+JZ3bNeLj4/H+vXrMWLECHTp0gXPPvsssrOzMWXKFERGRmLixIkoKChQtz9+/DgSExMRHR2NhIQEhydHW7duxZAhQxAZGYl+/fqpJ1fJsnvrrbfQvXt3xMXF3XARlXQz+8rLy8P06dMRFRWF0aNH4+LFi04/x2Kx4KmnnkLXrl0RHR2N+++/H9nZ2Vi1ahWOHTuGJUuWIDIyEkuWLAEAfPPNNxg8eDDuvvtuLFmyxOFpVUlbtmzBc889h+PHjyMyMlJtGfzoo48wYMAAxMbGYvr06bhy5Yr6nnbt2uH999/HwIEDMXDgQPzf//0fAGDkyJGIjIzE7t27S21lK/m0fcGCBVi8eDGmTp2KyMhIjBkzxuH4K3JelWXv3r1o27YthgwZAj8/Pzz66KNITU3FuXPnAADbt2/HzJkz0aBBA/zlL3/BmDFjyuxa+dFHH6nf99ChQ/Hzzz+r+Z0wYQKio6MxbNgwfPnll+p7FixYgOeff149VxMTE3H16lUsW7YMMTExGDx4MH755Rd1+/j4ePzzn//E0KFDERMTg2eeeQYWiwVA0Y/ntGnT0K1bN8TExGDatGm4fPmy+t4JEybg1VdfRWJiovpENTc3FwAwdepUvPfeew7HM2LECHzxxRc3HGfxE9XNmzcjLi4OcXFxDhXG6tWrMWfOHDz11FOIiorCJ598AqvVimXLlqnbL1u2DFarFb///jsGDx4MAIiJicGDDz4I4H/nw+bNm5GSkoINGzYgMjIS06dPB1D0m9SrVy+1JfTw4cM35PP111/HmjVr8NlnnyEyMhJbtmzBtm3bkJiYiBdffBGxsbFYvXo1FEXBmjVr0LdvX3Tv3h3z589HYWGhw7Fu3boVffr0QUxMDD788EOcOHECI0aMQHR0tHpdlaZNmzYYM2YM2rZte0Pa+fPnkZWVhYkTJ0Kr1aJ79+6IiorCp59+6nR/lXHu3DksWrRIvY6jo6MBAIWFhZg/fz66deuGvn37Ys2aNVAUpdR9jBs3DtHR0dDpdGjatClGjBiB//73vwAAo9GI//znP5g7dy6CgoIQHR2N+Ph49ThSUlIQHx+PmJgYBAUFYe7cudi7dy/0er1bj9OTWB//D+tj1seVwfr45urjLVu24J577sFDDz0EwPl1tWvXLtx3330O+3j77bfVutVqtWLFihW455570KNHDyxcuBBmsxlA+dfJ9T03rj+3yjpXDhw4gKFDhyIyMhK9evXChg0bbjjWb7/9FpMmTUJWVhYiIyOxYMECp8f/5ZdfYtiwYYiOjsaECRPU86j4e6vIb1RJOp0OEydORHR0NDSaG0PEffv2YcqUKQgICECLFi0wevToMn+XKmv8+PEAiu6bIiMj8eOPP5Z5L3O9Pn36YMiQIahXrx4CAgIwfvx4tU4Hiq63SZMmoVmzZmjatCkefvhh9Xr7/vvvYbfb8dBDD0Gn0+HBBx+EEALfffdd5Q9IeJG+ffuKb775RgghxNatW8Wdd94pNm/eLOx2u3j//fdFz549haIoQgghHnnkETF37lyRn58vrFarOHLkiBBCiO+++0506NBBJCUlCYvFIkwmkzh16pTo1q2bOH78uLDb7WLbtm2ib9++wmKxCCGE2L17t7h8+bKQZVns2rVLdO7cWVy5ckUIIcTjjz8u1qxZI2RZFmazWRw9elQIIYTBYBC9e/cWH3/8sbDZbOLUqVMiNjZWnDlzptRjGz9+vPjoo49cOrbSymXMmDHi6tWr4vLly6Jbt25i1KhR4ueffxYWi0VMmDBBrF69WgghxOXLl0VsbKz46quvhCzL4tChQyI2Nlbk5OQIIYTYv3+/SEtLE4qiiCNHjoiIiAhx6tQph7J79dVXhdVqFV999ZWIiIgQ+fn5pebrZvb12GOPiTlz5giDwSB+/fVXERcXJxITE0v9nA8//FBMmzZNGI1GYbfbxcmTJ0VhYeEN5SqEEDk5OSIyMlJ89tlnwmq1io0bN4oOHTo4bFPS1q1bHT7322+/FbGxseLUqVPCYrGIJUuWiHHjxqnpd9xxh5g4caLIy8sTJpNJ/duFCxec7vP6bZ5++mkRExMjfvrpJ2Gz2cQTTzwhHnvsMSFExc+r4n3FxMSIe++9V+zZs0dNe+GFF8TChQsdth82bJjYs2ePyM/PF3fccYe4evWqmvbZZ5+J4cOHl/o5u3fvFnFxceKnn34SiqKICxcuiD/++ENYrVbRv39/sXbtWmGxWMS3334runTpIs6dO6fmLzY2Vpw8eVKYzWYxYcIE0bdvX/HJJ58Iu90uXnnlFTF+/Hj1c/r27SuGDRsmMjIyRF5enhg7dqx45ZVXhBBC5Obmij179gij0SgKCwvFo48+KmbMmKG+d/z48aJfv37i/PnzwmQyifHjx4uVK1cKIYTYtWuXGD16tLrt6dOnRWxsrPobUFJ6erq44447xOOPPy4MBoNITU0VXbt2VX+bXn/9dXHnnXeKvXv3ClmWhclkEq+++qoYM2aMyM7OFjk5OWLs2LFi1apVDvuz2WxOz4fiYxRCiHPnzonevXuLy5cvq+9PS0sr9Xt5/fXXxZNPPqm+3rp1q+jQoYN49913hc1mEyaTSWzZskX0799fXLx4Uej1ejFr1izx1FNPOeTt73//uzCbzeLgwYOiU6dOYsaMGSI7O1v9vSn+fXXmwoUL4o477nD4W2pqqujSpYvD79rEiRPFzJkzHT47Li5O9OrVSyxYsED9nSouF2fn9vVKu+bmzZsnpk+fLgoLC0V6eroYOHCg09+B682YMUM9d37++Wdx1113OaSvX79eTJs2TQghxPTp08U///lPh/QuXbqIkydPCiGKzsuuXbuK2NhYMXbsWPHdd9+5lAdPY33M+rg0rI9ZHwtR/fXxvHnzhMFgECaTqczrymg0ii5duojff/9d3cd9990ndu7cKYQQYunSpWLatGkiLy9PFBYWimnTpomXXnpJCFH+dXL9+V3y3CrvXOnZs6f6e5Wfn69em9f77rvvRK9evco8/vPnz4vOnTuLQ4cOCavVKt58803Rv39/tfwq8htVll69et1QX8XGxoqffvpJfb1mzRoRHR2tvu7bt6/o3r276Nq1q3j44YfF6dOnHcqrc+fOIjY2VgwcOFC88cYbDvdFJZV231TWvUx5Nm7cKMaMGaO+joqKEsePH1dfnzhxQnTp0kXddvLkyQ7vnzp1qtiwYYMQoui+KyoqSsTExIihQ4eK999/v9zP99qWbQBo3rw5HnjgAWi1Wtx77724evUqsrOzkZWVha+//hqLFy9GgwYN4Ovri9jYWPV9Go0Gc+bMgU6ng7+/Pz766COMHTsWnTt3Vvfl6+uL48ePAyjqDtC0aVNoNBoMHToUrVq1wokTJwAUdZPMyMhAVlYW/Pz81FaTr776CuHh4bj//vvh4+ODjh07YtCgQS53EXR2bM6MHz8ejRo1QtOmTREdHY2IiAjceeed0Ol0GDBggPo08tNPP0Xv3r3Rp08faDQa9OzZE506dVKf1N9zzz249dZbIUkSYmNj0bNnTxw7dkz9HB8fH8yaNQu+vr7o06cPAgMDb+j2Wayy+5JlGf/5z38wZ84cBAYG4o477ihz/JyPjw/y8/ORlpYGrVaLTp06oV69eqVu+/XXX+P222/H4MGD4evri4ceegiNGjVy/kVcJyUlBffffz86duwInU6HJ554AsePH8cff/yhbjN16lQEBwfD39/f5f1eb8CAAYiIiICPjw8SEhLU8SAVPa8mTJiAzz//HN9++y3mzp2LBQsW4IcffgBQ1CJXv359h+3r1asHg8EAo9EIAA7p9evXh8FgKPVzPv74Y0yZMgURERGQJAmtWrVCeHg4fvrpJxiNRkydOhU6nQ7du3dH3759sWvXLodj7dSpE/z8/DBgwAD4+flh1KhR0Gq1GDp0qMNYGAD4v//7P4SFhSE4OBgzZsxQ99WwYUMMGjQIAQEBqFevHmbMmIGjR486vPe+++7DbbfdBn9/fwwePFjdd//+/ZGWloYLFy4AKLpOhgwZAp1O5/Q7mjVrFgIDA9GuXTvcd9992Llzp5rWpUsX9O/fHxqNBv7+/khJScGsWbMQGhqKkJAQzJo1Czt27HC677JotVpYrVacO3cONpsNLVq0wK233ury+5s0aYIJEybAx8dHzdvEiRPRsmVLBAUF4YknnsDu3bsduqPNmjULfn5+iIuLQ2BgIIYPH47Q0FD196Zka4er2rRpg5CQEKxfvx42mw2HDh3C0aNH1VaEhg0b4uOPP8b+/fuxbds2GAwGzJs3T31/Wed2eWRZxu7du/Hkk0+iXr16aNGiBR5++GGXvpOtW7fi1KlT6liz0q6jktdKWdcZADz11FP44osvcPDgQYwdOxbTp08vs+XQW7E+/h/Wx6yPS8P6uOrq40cffRSBgYHw9/cv87oKCAhAv3791Pr6woULOH/+POLj4yGEwJYtW/Dss88iODgY9erVw7Rp0xzKpyLXXEnlnSs+Pj747bffoNfr0aBBA3Ts2LHcfTo7/t27d6NPnz7o2bMnfH19MXnyZJjNZvz444/q9q7+RlVUr1698Oabb0Kv1yMtLQ1bt26FyWRS01euXKl23e7atSsmT56Ma9euAShqpU5JScHhw4fx+uuvY9euXaW28Dvjyr1MaVJTU7FmzRrMnz9f/ZvRaHT43apfvz6MRiOEEDAYDGXW6UOGDMHu3btx+PBhvPDCC1izZo3D/WFpSh/o5yVK/igHBAQAKCqggoICNGjQAA0aNCj1fQ0bNoSfn5/6OiMjA9u3b8e///1v9W82m00dLL99+3Zs3LhRnazCaDQiLy8PADBv3jy89tprGD16NBo0aICHH34Yo0ePxqVLl3DixAm1sgeKbvASEhJu6thc2d7Pz8/htb+/v/rejIwM7NmzB/v371fT7Xa7Oi7iwIEDSE5OxoULF6AoCsxmM+644w512+DgYIfxnwEBAU7zVdl95ebmwm63IywsTE1r3ry502MfOXIkLl++jCeeeALXrl1DQkICHn/8cfj6+t6wbVZWFpo1a6a+liTJ4XPKk5WV5fAjGBQUhODgYFy5cgUtWrQAgArtzxln319Fz6uSee3Tpw9GjBiBvXv34u6770ZgYOANXVkNBgOCgoLUMXF6vV69VvR6PYKCgkr9nMzMzFIDvuLyLtndqHnz5g5d/UqOPfL393d67MWuPy+Kr1OTyYTly5fj4MGDahcog8EAWZbVcXElxxiVPHd1Oh0GDx6MHTt2YPbs2di5c2e5E4qVzEd4eDjOnDmjvi55jhWXQ8lzuGS+K6pVq1Z49tlnsXr1avz222+Ii4vDggUL0LRpU5feX1rewsPD1dfh4eGw2+3IyclR/1byO/Lz87vhdVm/Tc74+voiOTkZS5cuxfr169GpUycMHjxYvaEKCgrCXXfdBaDoevj73/+OuLg46PV61KtXr8xzuzx5eXmw2Ww3fCclz8vSfPHFF3j55ZexceNGhISEAECp11HJa6W89M6dO6t/v/fee7Fz504cOHAAEyZMKPc4vAnr49K3Z33M+rgY6+Oqq49LnkflXVcjRozAP/7xD3Xf/fv3R0BAAHJycmAymRy6mQshHIYXVeSaK6m8c+X111/H2rVr8fLLL6Ndu3Z48sknERkZWe5+Szv+6+83NBoNwsLCHL5nV3+jKuq5557DCy+8gEGDBiE4OBjDhg1zeFhRsn6eNm0aPvnkExw7dgzx8fEO45rbtWuHWbNmYcOGDZg2bZpLn13WvYyz+6O0tDQ88sgjePbZZx2+m8DAQIeHWXq9HoGBgZAkCUFBQU6vVQAO8+9ERUXhwQcfxOeff47hw4c7zbtXB9vONGvWDAUFBbh27RpuueWWG9IlSXJ4HRYWhunTp2PGjBk3bHvp0iU899xzePvttxEZGQmtVouRI0eq6Y0bN8bSpUsBAMeOHcPDDz+MmJgYhIWFISYmxutmjAwLC8PIkSPVPJdUPMvgihUr0K9fP/j6+mLmzJlOx1CV5Wb2FRISAh8fH2RmZuIvf/kLgKLKwxlfX1/Mnj0bs2fPxh9//IGpU6fitttuw5gxY27YtnHjxg7jhoQQZe77ek2aNHGYIdRoNCI/P9/hQr7+/LpeQECA2noHAFevXnX582/2vJIkSf0O2rZt6zDmy2g04uLFi7j99tvRoEEDNG7cGKmpqeryEqmpqU4n8QoLCyu1Na5Jkya4fPkyFEVRK/jMzEy0bt26Uvkvfn+xjIwMNGnSBADw1ltv4ffff8dHH32Exo0b4/Tp0xg1apTL5++9996L+fPn4+6770ZAQEC5FV3J87NkPoAbz4EmTZogIyNDHbucmZnpsH1ZSjufRowYgREjRkCv12PhwoV46aWXsHLlykrt7/pzOiMjAz4+PggNDXW4VqpC+/btHYKqxMREjBo1qtRti/Pt7PsseW47e2+xhg0bwtfXFxkZGeo5nZmZWeYDi6+//hrPPfcc3nzzTYeZ1Vu3bg1ZlnHhwgX1vC55rbRt29ZhzHF6ejpsNpvTa6Cs46iJWB87x/qY9THr49JVtD4u+T2XdV0BQM+ePZGXl4fTp09j586d6lwRDRs2hL+/P3bt2uXyw+uSAgICHFpxS/Z+Ke9ciYiIwNq1a2Gz2fD+++/jscceK3NuiOuVPP4mTZo4PPwvvq4qc0wVFRwcjJdffll9/corryAiIsLp9uXV267W6UDZ9zKluXTpEh5++GHMnDnzhvuO4nq7OO+pqanq/dvtt9+Ot956C0IINR+//vorxo0b5/Q4yzvvvbobuTNNmjRB7969sXjxYhQUFMBms93QfaWkMWPGYNOmTfjpp58ghIDRaMRXX30FvV4Pk8kESZLUVoytW7eqs8wCwGeffaZWFg0aNIAkSdBoNLjnnntw4cIFbN++HTabDTabDSdOnHCYpMATEhISsH//fhw8eBCyLMNiseDIkSO4fPkyrFYrrFarWrkeOHCg0ksL3My+tFotBgwYgDfeeAMmkwm//fZbmROBfPfdd/j1118hyzLq1asHHx8f9clpo0aNHKbc79OnD86ePYv//Oc/sNvtePfdd8vsDni9ESNGYNu2bTh9+jSsVqv6Q1L8FL001+ehffv2OHv2LE6fPg2LxXLD0ghlqeh5tWfPHhgMBiiKgkOHDmHHjh2Ij48HUNRd7OzZs/j8889hsViQnJyMdu3aqTdUo0aNwtq1a1FQUIBz585hy5YtTrsPjh49Gm+99RZOnToFIQTS0tJw6dIlREREICAgQO0qfOTIEezbtw9Dhw51+Ziv98EHH+Dy5cvIz89XJ2cBip4s+vn54ZZbbkF+fj7eeOONCu03MjISGo0G//jHP1xq8VqzZg1MJhPOnj2Lbdu2lXlMw4YNw9q1a5Gbm4vc3FwkJydjxIgRLuUrNDTUoVvk+fPncfjwYVitVuh0Ovj5+d3ULNzDhw/HO++8g/T0dBgMBqxatQpDhgxxOoN5RQghYLFYYLPZABRNnlRyxs7U1FRYLBaYTCZs2LABWVlZaqvCTz/9hPPnz0NRFOTl5WHp0qWIjY1Vu2+VdW5fLzQ0FFeuXFE/W6vVYvDgwVi1ahX0ej0uXbqEjRs3Ov3eDx8+jHnz5mH16tU33DgEBgZiwIABeP3112E0GvHDDz/gyy+/VIPAESNGYP/+/Th27BiMRiNee+01DBgwAPXq1cO1a9dw8OBBWCwW2O127NixA8eOHUNcXNxNlLp3YX3sHOtj1sesj0tX0fq4pLKuK6Coy/agQYOQlJSEgoIC9QGGRqPBmDFj8OKLL6o9u65cuYKDBw+69LkdOnTA3r17YTKZkJaW5rA8XVnnitVqxY4dO1BYWAhfX18EBQXdVJ0+ZMgQHDhwAIcPH4bNZsNbb70FnU5XoZbyslitVnUiPJvNBovFogaTFy9eRF5eHmRZxoEDB7B582b1wWlGRgZ++OEH9f3r169HXl4eoqKiABT1vim+/s+dO4c1a9agX79+peYhJCQEGo3G4VquyL3MlStX8NBDD2HcuHGlLgs6cuRIbNy4EVeuXMGVK1ewceNG9XqLjY2FVqvFu+++C6vVqjYYdOvWDUBRD7iCggIIIXDixAm89957To+jWI0MtgEgKSkJPj4+GDJkCHr06IF33nnH6bZ33XUXXnjhBSxZsgQxMTEYOHAgtm3bBqDoCcakSZOQmJiIHj164MyZM+qJAQAnT57EmDFjEBkZiRkzZuBvf/sbWrZsiXr16mHDhg3YvXs3evXqhbi4OLz00ksON5qeEBYWhjVr1uCf//wnunfvjj59+mDDhg1QFAX16tXDc889h8ceewwxMTHYuXOn05vX8tzsvhYuXAij0YiePXtiwYIFN8weWVJ2djbmzJmDu+++G0OHDkVsbKz641zcfSMmJgZLly5FSEgIXnvtNbz88svo2rUr0tLSHL7P8nTv3h1z587Fo48+iri4OKSnp5e7BvLs2bOxYMECREdHY/fu3bjtttswa9YsTJw4EQMHDnSp22uxip5X7777Lnr37o3o6GgkJSVh6dKlaleqkJAQrF69GqtWrUJMTAxOnDiBV155RX3vnDlz0LJlS/Tt2xcTJkzA5MmT0bt371I/Z8iQIZg+fTqefPJJREVFYdasWSgoKIBOp8PatWvx9ddfo1u3bli8eDGSkpLUG4jKGD58OCZNmoT+/fujZcuW6g/5Qw89BIvFgm7dumHs2LHo1atXhfc9cuRInDlzxqG1zJnY2FgMGDAAEydOxKRJk8oMkGbOnIlOnTohISEBCQkJ6Nixozojc3lGjx6N3377DdHR0eryEsXnb1xcHHJzcx2WiKmo+++/HwkJCRg/fjz69esHnU6Hv//975XeX0nFN3jDhg0DUPT0vnj2daBoLF5cXBx69OiBw4cPY+PGjWo38vT0dEyZMgVRUVEYMWIEdDqdw/lZ1rl9vW7duuH2229HXFycus3f//53BAQEoH///hg3bhyGDx+O+++/v9T3r1mzBoWFheqMxJGRkZgyZYqavmjRIpjNZvTo0QNPPvkknn/+efUpeNu2bbF48WI89dRT6NGjBwwGAxYtWgSgqGvjq6++im7duvHM3koAACAASURBVKFbt27497//jeTkZLRp06ayRe6VWB+XjvUx62PWx85VpD4uqazrqtiIESPw7bffYvDgwQ7B2Lx589CqVSs88MADiIqKwsSJE10akw0UHbOvry969OiBp59+2uGBennnyqeffor4+HhERUVh06ZNSEpKqtAxl9SmTRusXLkSL7zwArp164b9+/dj3bp1ZY55r4jBgwcjIiICV65cweTJkxEREaG2KJ86dQojRoxAVFQUXnnlFbz00ktqXWgwGPD8888jNjYWvXv3xsGDB/Gvf/0LDRs2BFD0oC4hIQFdunTB1KlTMWDAAKddyAMCAjB9+nT89a9/RXR0NI4fP16he5ktW7YgPT0dycnJDuthF0tMTETfvn3VXoR9+vRBYmIigKJhDsnJyfj0008RHR2NrVu3Ijk5WS3f3bt3Y+DAgYiKisL8+fPxyCOPlDnPBQBIojb1ZyOiGi0+Ph5Lly5Fjx49qmT/27dvx+bNm/Hhhx863eaPP/5Av3798PPPP7ul9ZeIiKim8Yb6mKg2qLEt20REFWEymfDBBx9g7Nixns4KERFRncX6mOoSBttEVOsdPHgQ3bt3R2hoaJkzRhIREVHVYX1MdQ27kRMRERERERG5GVu2iYiIiIiIiNyMwTYRERERERGRmzHYJiIiIiIiInIzrmtTjrw8AxTFe4a1h4bWQ06O3tPZqBFYVq5hObmOZeWaqionq6zAVyNBkqQKvU+jkdCwYZDb80PehfV1zcWycg3LyXUsK9d4WznVxvqawXY5FEV4VeUNwOvy481YVq5hObmOZeWaqigni0UGdBr4aNgpi27E+rpmY1m5huXkOpaVa7ypnCr6ML0m4B0LERF5PUkCbLICWfae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\n",
      "text/plain": [
       "<Figure size 1008x288 with 2 Axes>"
      ]
     },
     "metadata": {},
     "output_type": "display_data"
    }
   ],
   "source": [
    "def plot_with_std(x, y, stds, ax, title, y_label):\n",
    "    ax.fill_between(x, y - stds, y + stds, alpha = 0.2)\n",
    "    plot(x, y, ax, title, y_label)\n",
    "fig, (ax1, ax2) = plt.subplots(ncols= 2)\n",
    "title = 'Increase in mean and std fortune 500 company %s from 1955 to 2005'\n",
    "stds1 = group_by_year.std().profit.values\n",
    "stds2 = group_by_year.std().revenue.values\n",
    "plot_with_std(x, y1.values, stds1, ax1, title % 'profits', 'Profit (millions)')\n",
    "plot_with_std(x, y2.values, stds2, ax2, title % 'revenues', 'Revenue (millions)')\n",
    "fig.set_size_inches(14,4)\n",
    "fig.tight_layout()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.4"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}

