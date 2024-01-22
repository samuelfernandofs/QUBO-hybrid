# QUBO-hybrid
Python Quantum framework for building hybrid asynchronous decomposition samplers for quadratic unconstrained binary optimization (QUBO) problems

Full QUBO Solver

We've defined a basic QUBO formulation for solving instances of the Vehicle Routing Problem (VRP). The formulation is inspired by a similar one for the Traveling Salesman Problem (TSP)

Let's define the binary function

\[ A(y_1, y_2, ..., y_n) = \sum_{i=1}^{n} \sum_{j=i+1}^{n} 2 y_i y_j - \sum_{i=1}^{n} y_i, \]

where

\[ A(y_1, y_2, ..., y_n) = \sum_{i=1}^{n} \sum_{j=i+1}^{n} 2 y_i y_j - \sum_{i=1}^{n} y_i, \]

By definition of VRP, the problem of minimizing the total cost can be defined as minimizing the function:

\[ (1) \quad C = \sum_{i=1}^{N} \sum_{j=1}^{N} c_{ij} \sum_{k=1}^{K} x_{ijk} + \sum_{i=1}^{N} c_{i0} \sum_{k=1}^{K} x_{i0k} + \sum_{k=1}^{K} u_k, \]

where \( c_{ij} \) is the cost of traveling from customer \( i \) to customer \( j \), \( c_{i0} \) is the cost of traveling from customer \( i \) to the depot, \( x_{ijk} \) is a binary variable indicating whether vehicle \( k \) travels from customer \( i \) to customer \( j \), and \( u_k \) is an auxiliary variable to ensure each vehicle returns to the depot after serving customers.

To ensure that each delivery is served by exactly one vehicle and exactly once, and that each vehicle is in exactly one place at a given time, the following term (in which all components \( A \) are equal to 1) is added:

\[ (3) \quad \sum_{i=1}^{N} A(y_{i1}, y_{i2}, ..., y_{iK}) = 1, \]

where \( y_{ik} \) is a binary variable indicating whether customer \( i \) is served by vehicle \( k \).

By definition of VRP, the QUBO representation of this optimization problem is:

\[ (5) \quad Q_{\text{VRP}} = Q_{\text{cost}} + Q_{\text{assignment}}, \]

where \( Q_{\text{cost}} \) and \( Q_{\text{assignment}} \) are the coefficient matrices associated with the cost and assignment components, respectively, and \( \alpha \), \( \beta \), and \( \gamma \) are constants specific to the problem.
