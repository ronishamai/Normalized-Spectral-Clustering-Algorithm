## Overview
This project implements the Normalized Spectral Clustering algorithm. The project consists of multiple files including Python and C programs, and it integrates the C extension with Python to perform various matrix calculations efficiently. The main tasks were to calculate the Weighted Adjacency Matrix, Diagonal Degree Matrix, Normalized Graph Laplacian, eigenvalues and eigenvectors using the Jacobi algorithm, and to perform full spectral clustering.

## Files and Directories

### Python Files
- **spkmeans.py**: This is the main Python interface that reads user command-line arguments, implements k-means++ for clustering, and interfaces with the C extension.
- **setup.py**: The build script for creating the C extension module.
- **comp.sh**: A shell script to compile the C program.

### C Files
- **spkmeans.h**: Header file defining function prototypes used in spkmeansmodule.c and implemented in spkmeans.c.
- **spkmeans.c**: The main C program implementing the required algorithms for matrix calculations.
- **spkmeansmodule.c**: The Python C API wrapper to interface with the C implementation from Python.

### Additional C Headers and Modules
- **Additional .c/.h files**: You may include additional C source and header files as needed to modularize your code.

## Compilation and Setup

### Compiling the C Program
To compile the C program independently, use the provided shell script:
bash comp.sh

### Building the Python C Extension
To build the Python C extension, run:
python3 setup.py build_ext --inplace

## Running the Program
To execute the program, use the following format:
python3 spkmeans.py <k> <goal> <file_name>

Where:
- **k**: Number of clusters. If k=0, the eigengap heuristic will be used to determine the number of clusters.
- **goal**: The task to perform. It can be one of the following:
  - `spk`: Perform full spectral k-means clustering.
  - `wam`: Calculate and output the Weighted Adjacency Matrix.
  - `ddg`: Calculate and output the Diagonal Degree Matrix.
  - `lnorm`: Calculate and output the Normalized Graph Laplacian.
  - `jacobi`: Calculate and output the eigenvalues and eigenvectors using the Jacobi algorithm.
- **file_name**: The path to the input file containing the data points (for all goals except Jacobi) or a symmetric matrix (for Jacobi).

## Error Handling
- In case of invalid input, the program will print "Invalid Input!" and terminate.
- For any other errors, the program will print "An Error Has Occurred" and terminate.

## Assumptions and Requirements
1. The input files are correctly formatted.
2. Algorithmic implementations are in C, except for k-means++ which is in Python.
3. Command line arguments are validated for correctness.
4. Output should be formatted to 4 decimal places.
5. The Jacobi algorithm runs up to 100 iterations if it does not converge earlier.
6. Code should be modular, reusable, and well-commented.
7. Handle memory allocation and deallocation properly.
8. Data dimensionality is assumed to be up to 1000 points and up to 10 features.
9. All data points are unique.
10. Use double in C and float in Python for vector elements.
