# AoA-assignment-no-04
#This repository is created for the source code of sorting, related with this assignment

import time
import matplotlib.pyplot as plt
import numpy as np

# Bubble Sort implementation
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

# Arrays given
arr1 = list(range(1, 6))
arr2 = list(range(1, 11))
arr3 = list(range(1, 51))
arr4 = list(range(1, 101))

arrays = [arr1, arr2, arr3, arr4]
array_sizes = [len(arr) for arr in arrays]

average_times = []

# Measure execution time
def measure_time(arr):
    runs = 5
    times = []
    for _ in range(runs):
        temp = arr.copy()
        start = time.time()
        bubble_sort(temp)
        end = time.time()
        times.append((end - start) * 1e6)  # convert to microseconds
    return np.mean(times)

for arr in arrays:
    avg_time = measure_time(arr)
    average_times.append(avg_time)

# Print results
print("Input Size | Average Time (microseconds)")
for size, t in zip(array_sizes, average_times):
    print(f"{size:10} | {t:.2f}")

# Plotting
plt.figure(figsize=(8,6))
plt.plot(array_sizes, average_times, marker='o', linestyle='-')
plt.title('Bubble Sort: Input Size vs Execution Time')
plt.xlabel('Input Size (N)')
plt.ylabel('Average Execution Time (microseconds)')
plt.grid(True)
plt.show()
