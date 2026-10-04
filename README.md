Practical No 1
# Stack Implementation using List in Python

stack = []

# Push elements
stack.append(10)
stack.append(20)
stack.append(30)

print("Stack:", stack)

# Peek at the top element
print("Top element:", stack[-1])

# Pop an element
removed = stack.pop()
print("Popped element:", removed)

print("Stack after pop:", stack)

# Check if stack is empty
if len(stack) == 0:
    print("Stack is empty")
else:
    print("Stack is not empty")
.............................................................................

Practical No 2
Practical 2(A)
1. Queue Using Array (Python List) 
queue = []

# Enqueue elements
queue.append(10)
queue.append(20)
queue.append(30)

print("Queue:", queue)

# Dequeue an element
removed = queue.pop(0)
print("Dequeued element:", removed)

print("Queue after dequeue:", queue)

# Peek at the front element
print("Front element:", queue[0])

# Check if queue is empty
if len(queue) == 0:
    print("Queue is empty")
else:
    print("Queue is not empty")

    Practical 2(B)
2. Queue Using Linked List
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class Queue:
    def __init__(self):
        self.front = None
        self.rear = None

    # Enqueue
    def enqueue(self, data):
        new_node = Node(data)

        if self.rear is None:
            self.front = self.rear = new_node
        else:
            self.rear.next = new_node
            self.rear = new_node

    # Dequeue
    def dequeue(self):
        if self.front is None:
            print("Queue is empty")
            return

        removed = self.front.data
        self.front = self.front.next

        if self.front is None:
            self.rear = None

        print("Dequeued:", removed)

    # Display
    def display(self):
        temp = self.front
        while temp:
            print(temp.data, end=" ")
            temp = temp.next
        print()

q = Queue()
q.enqueue(10)
q.enqueue(20)
q.enqueue(30)

print("Queue:")
q.display()

q.dequeue()

print("Queue after dequeue:")
q.display()

................................................................................

Practical No 3 
Singly Linked List Operations: Write a program to
implement a Singly Linked List with the following
operations:
● Insert at beginning
● Insert at end
● Insert at given position
● Delete from beginning
● Delete from end
● Search an element
● Display list

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class SinglyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at beginning
    def insert_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    # Insert at end
    def insert_end(self, data):
        new_node = Node(data)

        if self.head is None:
            self.head = new_node
            return

        temp = self.head
        while temp.next:
            temp = temp.next

        temp.next = new_node

    # Insert at given position
    def insert_position(self, data, position):
        new_node = Node(data)

        if position == 1:
            new_node.next = self.head
            self.head = new_node
            return

        temp = self.head

        for i in range(1, position - 1):
            if temp is None:
                print("Invalid position")
                return
            temp = temp.next

        if temp is None:
            print("Invalid position")
            return

        new_node.next = temp.next
        temp.next = new_node

    # Delete from beginning
    def delete_beginning(self):
        if self.head is None:
            print("List is empty")
            return

        self.head = self.head.next

    # Delete from end
    def delete_end(self):
        if self.head is None:
            print("List is empty")
            return

        if self.head.next is None:
            self.head = None
            return

        temp = self.head
        while temp.next.next:
            temp = temp.next

        temp.next = None

    # Search an element
    def search(self, key):
        temp = self.head
        position = 1

        while temp:
            if temp.data == key:
                print("Element found at position", position)
                return

            temp = temp.next
            position += 1

        print("Element not found")

    # Display list
    def display(self):
        temp = self.head

        if temp is None:
            print("List is empty")
            return

        while temp:
            print(temp.data, end=" -> ")
            temp = temp.next

        print("None")


# Create linked list
list1 = SinglyLinkedList()

# Insert operations
list1.insert_beginning(20)
list1.insert_beginning(10)
list1.insert_end(30)
list1.insert_position(25, 3)

print("Linked List:")
list1.display()

# Search
list1.search(25)

# Delete from beginning
list1.delete_beginning()
print("After deleting from beginning:")
list1.display()

# Delete from end
list1.delete_end()
print("After deleting from end:")
list1.display()

................................................................................

Practical No 4
Binary Tree Traversals: Write a program to create a Binary
Tree. Implement Preorder, Inorder, and Postorder Traversals.

class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None


# Create Binary Tree
root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)


# Preorder: Root -> Left -> Right
def preorder(root):
    if root:
        print(root.data, end=" ")
        preorder(root.left)
        preorder(root.right)


# Inorder: Left -> Root -> Right
def inorder(root):
    if root:
        inorder(root.left)
        print(root.data, end=" ")
        inorder(root.right)


# Postorder: Left -> Right -> Root
def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" ")


# Display traversals
print("Preorder Traversal:")
preorder(root)

print("\nInorder Traversal:")
inorder(root)

print("\nPostorder Traversal:")
postorder(root)

...................................................................................

Practical No 5
Graph Representation and Traversals:
● Depth First Search (DFS)
● Breadth First Search (BFS)

1. DFS
   # Graph using adjacency list
graph = {
    0: [1, 2],
    1: [0, 3, 4],
    2: [0, 4],
    3: [1],
    4: [1, 2]
}

# DFS function
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()

    visited.add(start)
    print(start, end=" ")

    for neighbour in graph[start]:
        if neighbour not in visited:
            dfs(graph, neighbour, visited)

# Perform DFS
print("DFS Traversal:")
dfs(graph, 0)

2. BFS
# Graph using adjacency list
graph = {
    0: [1, 2],
    1: [0, 3, 4],
    2: [0, 4],
    3: [1],
    4: [1, 2]
}

# BFS function
def bfs(graph, start):
    visited = set()
    queue = [start]

    visited.add(start)

    while queue:
        vertex = queue.pop(0)
        print(vertex, end=" ")

        for neighbour in graph[vertex]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)

# Perform BFS
print("BFS Traversal:")
bfs(graph, 0)

.......................................................................................

Practical No 6
Shortest Path using Dijkstra's Algorithm: Implement
Dijkstra’s Algorithm to find the shortest path from a source
node to all other nodes in a weighted graph....

import heapq

def dijkstra(graph, source):
    distance = {node: float('inf') for node in graph}
    distance[source] = 0

    priority_queue = [(0, source)]

    while priority_queue:
        current_distance, current_node = heapq.heappop(priority_queue)

        if current_distance > distance[current_node]:
            continue

        for neighbour, weight in graph[current_node]:
            new_distance = current_distance + weight

            if new_distance < distance[neighbour]:
                distance[neighbour] = new_distance
                heapq.heappush(priority_queue, (new_distance, neighbour))

    return distance


# Weighted graph
graph = {
    'A': [('B', 4), ('C', 2)],
    'B': [('A', 4), ('C', 1), ('D', 5)],
    'C': [('A', 2), ('B', 1), ('D', 8)],
    'D': [('B', 5), ('C', 8)]
}

# Source node
source = 'A'

# Find shortest distances
result = dijkstra(graph, source)

print("Shortest distances from", source)
for node, distance in result.items():
    print(node, ":", distance)

...................................................................................................

Practical No 7 
Write a program to compute MST (Minimum Spanning Tree) for a connected graph using Prim’s Algorithm...

import heapq

def prim(graph, start):
    visited = set()
    min_heap = [(0, start)]
    mst = []
    total_cost = 0

    while min_heap:
        weight, node = heapq.heappop(min_heap)

        if node in visited:
            continue

        visited.add(node)
        total_cost += weight

        if weight != 0:
            mst.append((parent, node, weight))

        for neighbour, edge_weight in graph[node]:
            if neighbour not in visited:
                parent = node
                heapq.heappush(
                    min_heap,
                    (edge_weight, neighbour)
                )

    return mst, total_cost

# Weighted graph
graph = {
    'A': [('B', 2), ('C', 3)],
    'B': [('A', 2), ('C', 1), ('D', 4)],
    'C': [('A', 3), ('B', 1), ('D', 5)],
    'D': [('B', 4), ('C', 5)]
}

# Find MST
mst, total_cost = prim(graph, 'A')

print("Minimum Spanning Tree:")
for u, v, weight in mst:
    print(u, "-", v, ":", weight)

print("Total Cost:", total_cost)

.......................................................................................................

Practical No 8
Implementing and Analyzing Sorting Algorithms:
1.Bubble Sort,
2. Insertion Sort
3. Selection Sort

1.Bubble Sort...
def bubble_sort(arr):
    n = len(arr)

    for i in range(n):
        for j in range(0, n - i - 1):

            if arr[j] > arr[j + 1]:
                # Swap elements
                arr[j], arr[j + 1] = arr[j + 1], arr[j]

    return arr
    
# Input list
arr = [64, 34, 25, 12, 22, 11, 90]

print("Original list:", arr)

bubble_sort(arr)

print("Sorted list:", arr)

2. Insertion Sort
    def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1

        # Move elements greater than key
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1

        arr[j + 1] = key

    return arr

# Input list
arr = [64, 34, 25, 12, 22, 11, 90]

print("Original list:", arr)

insertion_sort(arr)

print("Sorted list:", arr)


3. Selection Sort
   def selection_sort(arr):
    n = len(arr)

    for i in range(n):
        min_index = i

        # Find the smallest element
        for j in range(i + 1, n):
            if arr[j] < arr[min_index]:
                min_index = j

        # Swap
        arr[i], arr[min_index] = arr[min_index], arr[i]

    return arr

# Input list
arr = [64, 25, 12, 22, 11]

print("Original list:", arr)

selection_sort(arr)

print("Sorted list:", arr)

...................................................................................

Practical No 9 
Sorting Algorithm Performance Comparison:

● Merge Sort
● Quick Sort

1.Merge Sort
def merge_sort(arr):

    if len(arr) > 1:
        mid = len(arr) // 2

        left = arr[:mid]
        right = arr[mid:]

        # Sort left and right parts
        merge_sort(left)
        merge_sort(right)

        i = j = k = 0

        # Merge the two sorted parts
        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                arr[k] = left[i]
                i += 1
            else:
                arr[k] = right[j]
                j += 1
            k += 1

        # Copy remaining elements
        while i < len(left):
            arr[k] = left[i]
            i += 1
            k += 1

        while j < len(right):
            arr[k] = right[j]
            j += 1
            k += 1


# Input list
arr = [38, 27, 43, 3, 9, 82, 10]

print("Original list:", arr)

merge_sort(arr)

print("Sorted list:", arr)

2.Quick Sort
def quick_sort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[0]

    left = [x for x in arr[1:] if x <= pivot]
    right = [x for x in arr[1:] if x > pivot]

    return quick_sort(left) + [pivot] + quick_sort(right)


# Input list
arr = [64, 34, 25, 12, 22, 11, 90]

print("Original list:", arr)

sorted_arr = quick_sort(arr)

print("Sorted list:", sorted_arr)

.........................................................................................................

Practical No 10 
Searching Techniques Comparison Implement:
● Linear Search
● Binary Search

1. Linear Search
   def linear_search(arr, key):
    for i in range(len(arr)):
        if arr[i] == key:
            return i

    return -1


# Input list
arr = [10, 20, 30, 40, 50]

key = 30

result = linear_search(arr, key)

if result != -1:
    print("Element found at position:", result + 1)
else:
    print("Element not found")

2. Binary Search
   def binary_search(arr, key):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == key:
            return mid

        elif arr[mid] < key:
            low = mid + 1

        else:
            high = mid - 1

    return -1


# Sorted list
arr = [10, 20, 30, 40, 50, 60, 70]

key = 50

result = binary_search(arr, key)

if result != -1:
    print("Element found at position:", result + 1)
else:
    print("Element not found")

...........................................................................................................



