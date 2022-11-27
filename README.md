# D-Wave-JSP
Demo program to solve a **Job Scheduling Problem** using a **Discrete Quadratic Model**.

## Problem Description
A set of jobs are described as a sequence of operations to be executed on machines. Each operation can require a given time, different from job to job.

The selection of which job start firsts, which precedence apply to access machines, etc, shall be done with the task of minimizing the overall time requested to complete all the jobs.

This is the more general definition of Job Scheduling Problem. In this example, we focus on a simplified version. Assuming that the scheduling can be arranged to have an overall execution time not bigger than **Tmax**, found a feasible schedule to satisfy it.

## Data Description
The set of jobs to be executed is defined in a dictionary:
1. Each job is identified by a key whihc is its name (*string*) and has a vector as value.
1. The vector contains the operations to be executed on each machine, in the proper order:
    1. Each entry of the vector is a tuple: (machine, time)
    1. The machine field (*string*) identifies the specific machine to be used
    1. The time field identifies the time needed to excute the operation on the machine (*integer*)

The Tmax value (*integer*) can be either defined in advance or left to the program to be calculate:
1. If set to zero, the program will set it. The program will assume jobs operating in parallel:
    1. First step: all the jobs execute their first operation. If they contend for any machine, they are executed one after the other. The total time be the maximum value among the all the machines.
    1. Same calculation for all the other steps (as long as the longest job).
    1. The overall time is the sum of all the steps. This is, by calculation, a feasible time.
1. If set to a positive integer, it will be used by the program.

