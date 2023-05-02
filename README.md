Download Link: https://assignmentchef.com/product/solved-comp1007-lab-5-handling-quantitative-dataintroduction-to-numpy
<br>
<em>1 What is NumPy?</em>

<strong><u>NumPy</u></strong> (standing for Numerical Python) is a popular library in Python that can efficiently process <strong>multidimensional data arrays</strong>. It is also the foundation of other advanced Python libraries such as <strong>Pandas</strong>.

Examples of 1‐dimensinoal array: the elements must have the same data type

<ul>

 <li>[2, 7, 10, 6] # an array of integers, shape is (4)</li>

 <li>[73.5, 67.0, 87.5, 58.5, 92.0] # an array of student grades or stock prices, shape is (5)</li>

 <li>[‘Sam’, ‘John’, ‘Zoe’] # an array of names, shape is (3)</li>

</ul>

Examples of 2‐diminsionial array: an array of array with the same shape and data type

<ul>

 <li>[ [3, 6, 4, 8],</li>

</ul>

[2, 7, 5, 9],

[4, 8, 6, 1] ]  # an array with 3 elements; each element is an array with 4 integers. Shape = (3, 4)

The major features of NumPy include:

<ul>

 <li>Easily generate and store data in memory in the form of multidimensional array</li>

 <li>Easily load and store data on disk in binary, text, or CSV format</li>

 <li>Support <strong>efficient</strong> operations on data arrays, including basic arithmetic and logical operations, shape manipulation, data sorting, data slicing, linear algebra, statistical operation, discrete Fourier transform, etc.</li>

 <li>Vectorised computation: simple syntax for elementwise operations without using loops (e.g., <strong>a</strong> = <strong>b</strong> + <strong>c</strong> where <strong>a</strong>, <strong>b</strong> and <strong>c</strong> are three multidimensional arrays with the same shape).</li>

</ul>




In order to use NumPy, we need to import the module <strong><u>numpy</u></strong> first. A widely used convention is to use <strong><u>np</u></strong> as a short name of <strong><u>numpy</u></strong>. In this labsheet, when you see <strong>np.xxx</strong>, it is the same as <strong>numpy.xxx</strong>. Remark: the module name of NumPy library is <strong>numpy</strong> (i.e., lowercase).

import numpy as np

<em>2 The data type of N‐dimensional array: ndarray </em>

The core of NumPy is the N‐dimensional array datatype <strong>ndarray</strong>. It can store a collection of data items <strong><u>with the same type</u></strong>, i.e., the array is <strong>homogeneous</strong>. This makes it very different from list. A list is more flexible, but less efficient. ndarray can only store items with the same type, but its performance is much better than list (i.e., it takes a shorter time to process the same amount of data).

An ndarray object has the following properties:

<table width="0">

 <tbody>

  <tr>

   <td width="142"><strong>ndarray.ndim</strong></td>

   <td width="454">The number of dimensions of the array (i.e., 1 or 2 or 3 …)</td>

  </tr>

  <tr>

   <td width="142"><strong>ndarray.shape</strong></td>

   <td width="454">The dimensions of the array (i.e., number of elements in each dimension)</td>

  </tr>

  <tr>

   <td width="142"><strong>ndarray.size</strong></td>

   <td width="454">The total number of elements of the array</td>

  </tr>

  <tr>

   <td width="142"><strong>ndarray.dtype</strong></td>

   <td width="454">The data type of the array</td>

  </tr>

  <tr>

   <td width="142"><strong>ndarray.itemsize</strong></td>

   <td width="454">The number of bytes of each data element</td>

  </tr>

  <tr>

   <td width="142"><strong>ndarray.data</strong></td>

   <td width="454">The buffer that stores the data elements of the array</td>

  </tr>

 </tbody>

</table>




NumPy supports the following popular data types:

<ul>

 <li>Integers with different sizes: int8 / int16 / int32 / int64 / uint8 / uint16 / uint32 / unit64</li>

 <li>Real numbers with different sizes: float16 / float32 / float64 / float128</li>

 <li>Complex numbers with different sizes: complex64 / complex128 / complex256</li>

 <li>bool</li>

 <li>Traditional ASCII string with constant length (one byte per character): S10 means a sting with 10 characters</li>

 <li>Unicode string with constant length: U10 means a string with 10 unicode characters</li>

</ul>

<strong>Example 1</strong>: Try the following statements about a two-dimensional array:

a = <strong>np.arange</strong>(20) # generate a one-dimensional array first print(a) # [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19] a = <strong>a.reshape</strong>(4, 5) # generate a two-dimensional array from a, and assign it to a print(a)  type(a) # numpy.ndarray print(a.ndim) # 2 print(a.shape) # (4, 5) print(a.dtype.name) # int32 print(a.itemsize) # 4 print(a.size) # 20




<strong>Exercise 1</strong>: Use numpy.arange() to generate a 1-dimenstional array with 100 odd numbers 1, 3, 5, …, 199. Then use numpy.reshape() to generate a two-dimensional array with shape (10, 10). Print out the shape, size, and data of the two-dimensional array.




<em>3 How to create ndarray objects? </em>

We will study four different approaches to creating ndarray objects.







<ul>

 <li>Use the <strong>numpy</strong>.<strong>array( )</strong> function to generate an ndarray object from any sequence-like object (e.g., list and tuple)</li>

</ul>




<strong>Example 2</strong>: Try the following statements about creating ndarrays from lists




<table width="0">

 <tbody>

  <tr>

   <td width="554"># import numpy as np#generate a one-dimensional array from a sequence of data data1 = [1, 2, 3, 4, 5, 6] arr1 = np.array(data1) print(arr1) print(arr1.ndim) print(arr1.shape)#generate a two-dimensional array from a sequence of sequence of datadata2 = [ [1, 2, 3, 4], [5, 6, 7, 8] ] arr2 = np.array(data2) print(arr2) print(arr2.ndim) print(arr2.shape)#generate a three-dimensional array from a sequence of sequence of sequence of datadata3 = [ [ [1, 2, 3, 4], [5, 6, 7, 8] ],[ [9, 10, 11, 12], [13, 14, 15, 16] ],                [ [17, 18, 19, 20], [21, 22, 23, 24] ] ] arr3 = np.array(data3) print(arr3) print(arr3.ndim) print(arr3.shape)</td>

  </tr>

 </tbody>

</table>







<ul>

 <li>Use the following functions to generate some special ndarray object. Use <strong>help( )</strong> to find out the details of each function.</li>

</ul>




<table width="0">

 <tbody>

  <tr>

   <td width="78"><strong>Function </strong></td>

   <td width="166"><strong>Example </strong></td>

   <td width="310"><strong>Description </strong></td>

  </tr>

  <tr>

   <td width="78"><strong>arange </strong></td>

   <td width="166">arr = np.arange(20)</td>

   <td width="310">Return evenly spaced values within a given interval, simiar to the built-in <strong>range( )</strong> function.</td>

  </tr>

  <tr>

   <td width="78"><strong>ones </strong></td>

   <td width="166">arr = np.ones(10)</td>

   <td width="310">An array of all 1’s with the given shape</td>

  </tr>

  <tr>

   <td width="78"><strong>zeros </strong></td>

   <td width="166">arr = np.zeros( (2, 3) )</td>

   <td width="310">An array of all 0’s with the given shape</td>

  </tr>

  <tr>

   <td width="78"><strong>full </strong></td>

   <td width="166">arr = np.full( (3, 4), 1.2)</td>

   <td width="310">An array of all specified value with the given shape</td>

  </tr>

  <tr>

   <td width="78"><strong>empty </strong></td>

   <td width="166">arr = np.empty( (2, 5) )</td>

   <td width="310">An array with the given shape without initial data</td>

  </tr>

 </tbody>

</table>

<strong>eye               </strong>arr = np.eye(6)                    A square NxN <strong><em>identity matrix</em></strong>




<strong>Example 3</strong>: Try the following statements to learn different array generating functions

arr = np.ones(10) print(arr) arr = np.zeros( (2, 3) ) print(arr) arr = np.full( (3, 4), 1.2) print(arr) arr = np.empty( (2, 5) ) print(arr) arr = np.eye(6) print(arr)




<ul>

 <li>Generate ndarray with random numbers (<strong>random sampling</strong>)</li>

</ul>

The <strong>numpy.random</strong> module provides functions to generate arrays of sample values from popular probability distributions.

<strong>Reference</strong>: <u>https://docs.scipy.org/doc/numpy/reference/routines.random.html</u>

<strong>Example 4</strong>: Try the following statements to generate different random arrays. Use <strong>help( )</strong> to understand the functions <strong>random()</strong>, <strong>randint()</strong>, <strong>randn()</strong>, and <strong>uniform()</strong> in numpy.random module.

help(np.random.random) #

<table width="0">

 <tbody>

  <tr>

   <td width="604">arr = <strong>np.random.random</strong>((2,3)) # Return 2×3 random floats in half-open interval [0.0, 1.0) print(arr) arr = <strong>np.random.randint</strong>(10, 100, 10) # Return 10 random integers in half-open interval [10, 100) arr = <strong>np.random.randn</strong>(6, 3) # Draw 6×3 samples from <strong>standard normal distribution</strong>print(arr) arr = <strong>np.random.uniform</strong>(-1, 1, 10) # Draw 10 samples from a <strong>uniform distribution</strong> in (-1, 1)print(arr)</td>

  </tr>

 </tbody>

</table>




<ul>

 <li>Save ndarray to disk file, and ndarray from disk file</li>

</ul>




<strong>Example 5</strong>: Try the following statements to save ndarray as <strong>binary file</strong> and load ndarray from binary file (which was previously created by <strong>numpy.save()</strong> function).

<ol>

 <li>Binary format (which is not suitable for human to read)</li>

</ol>

arr1 = <strong>np.arange</strong>(2, 100, 2) # Return an array of [2, 4, 6, …, 96, 98] with stepsize of 2 <strong>np.save</strong>(‘even.npy’, arr1) # save ndarray to file even.npy arr2 = <strong>np.load</strong>(‘even.npy’) # load data from even.npy and create an ndarray print(arr2)




<strong>Example 6</strong>: Try the following statements to save ndarray as <strong>txt file</strong> and load ndarray from txt file.

<ol>

 <li>Txt format (which is suitable for human to read)</li>

</ol>

arr1 = <strong>np.arange</strong>(0.0, 10.0, 0.5) <strong>np.savetxt</strong>(‘half.txt’, arr1, fmt=’%.6f’) # You can use a text editor to open half.txt arr2 = <strong>np.loadtxt</strong>(‘half.txt’) print(arr2)




<strong>Exercise 2</strong>: Create the following ndarray objects:

<ul>

 <li>Create an ndarray of shape (8, 8) and all data are 2.5</li>

 <li>Create an ndarray of shape (4, 4) whose values range from 0 to 15</li>

 <li>Create a 6 × 6 identity matrix</li>

 <li>Create a random array of size 20 with standard normal distribution and find its mean value</li>

 <li>Create a random array of shape (3, 6) with random integers in the range of [1, 50).</li>

 <li>Create a random array of shape (4, 5) with uniform distribution in the range of [0, 10). Find its maximum and minimum values and the mean value.</li>

</ul>

<em>4 How to access and manipulate data in ndarray? </em>

Accessing data in one-dimensional ndarray is similar to the case of list.

<strong>Array indexing</strong>: use the square brackets ([ ]) to index array values. To access a single data element in two-dimensional ndarray, you need to specify the coordinate of the element (i.e., the indices on the two axes).

If you index a multidimensional array with fewer indices than dimensions, you will get a sub-dimensional array.

<strong>Example 7</strong>: Try the following statements to access items in ndarray

arr2d = np.array([ [1,2,3], [4,5,6], [7,8,9] ]) arr1d = arr2d[2] print(arr1d) # [7, 8, 9] print(arr2d[1]) # [4, 5, 6]  arr2d[1][2] = 10 # we can change the values in ndarray print(arr2d[1]) # [4, 5, 10] print(arr2d[0][2]) # 3 print(arr2d[0,2]) # 3, the same as the previous print()




<strong>Slicing</strong>: Slicing on ndarray is similar to sequence slicing, but more complicated for 2 or 3-dimensions.

arr1d = np.arange(20) print(arr1d) arr1d[:10] = 20 # change of first 10 values in arr1d to 20 print(arr1d) arr1d[10:15] = -1 # change the next 5 values to -1 print(arr1d) arr1d[-5:] = 0 # change the last 5 values in arr1d to 0 print(arr1d)




<em> </em>

<em> </em>

<em>5 More data processing in ndarray </em>

(1) Universal functions: perform elementwise operations on data in ndarrays




Mathematical functions: <u>https://docs.scipy.org/doc/numpy/reference/routines.math.html</u>

<strong>Example 8</strong>: Try some vectorised operations and universal functions on ndarrays:

x = np.array([1, 2, 3, 4]) y = np.array([5, 6, 6, 8]) print(x+y) # [6 8 9 12] print(x*y) # [5 12 18 32] arr = np.arange(10) print(arr) # [0 1 2 3 4 5 6 7 9 9] print(<strong>np.sqrt</strong>(arr)) # [0.   1.    1.41421356 1.73205081 2.  2.23606798  … ] print(<strong>np.exp</strong>(arr))







(2) Statistics

Reference: <u>https://docs.scipy.org/doc/numpy/reference/routines.statistics.html</u>

<strong>Example 9</strong>: Try some statistical methods of ndarrays

arr = np.random.randn(20, 5)

print(arr) print(“The mean is”, <strong>arr.mean</strong>()) print(“The standard deviation is”, <strong>arr.std</strong>()) print(“The max and min are:”, <strong>arr.max</strong>(), <strong>arr.min</strong>()) print(“The index of the min is {} and the index of the max is {}”.format(<strong>arr.argmin</strong>(), <strong>arr.argmax</strong>()))




<em>Additional Resources: </em>

If you want to learn more about NumPy, please try the following series of tutorials: <u>https://www.tutorialspoint.com/numpy/index.htm</u>