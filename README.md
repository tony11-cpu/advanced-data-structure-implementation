# 🚀 Advanced Data Structures in C#

> A production-grade library of fundamental and self-balancing data structures implemented from scratch in C# — no external dependencies.

This repository contains hand-crafted implementations of core computer science data structures, showcasing a deep understanding of algorithmic complexity, self-balancing tree mechanics, and graph traversal strategies. Every structure is built with generics for type safety and reusability.

---

## 📦 What's Implemented

### 🌳 Self-Balancing Binary Search Trees

| Structure | Time Complexity (Average) | Key Features |
|-----------|---------------------------|-------------|
| **AVL Tree** | O(log n) insert/delete/search | Height tracking, LL/LR/RR/RL rotations, balance factor rebalancing |
| **Red-Black Tree** | O(log n) insert/delete/search | Color-based balancing, left/right rotations, O(1) height constraint |

Both support generic types with `Comparer<T>`, BFS/DFS traversals, and the standard BST operations you'd expect in production code.

### 📊 Heaps & Priority Queues

- **MinHeap<T>** — Binary min-heap with heapify-up/down operations
- **MaxHeap<T>** — Binary max-heap extracted from min-heap logic
- **MinPriorityQueue<T>** / **MaxPriorityQueue<T>** — Thread-safe wrappers around heaps

All support `Insert`, `ExtractMin/Max`, `Peek`, `Remove`, and `O(log n)` operations.

### 🕸️ Graphs & Pathfinding

- **Graph<T>** — Adjacency matrix-based implementation
  - Directed & undirected graphs
  - BFS & DFS traversals
  - In-degree & out-degree calculations

- **Dijkstra's Algorithm** — Two implementations:
  - Standard O(V²) version
  - **Optimized version** using `MinPriorityQueue` for O(E log V) performance

### 🌲 General Trees

- **Tree<T>** — N-ary tree structure for hierarchical data
- **BinaryTree<T>** — Complete binary tree with level-order insertion

### 🔍 Searching & Sorting

- **Linear Search** — O(n) simple scan
- **Binary Search** — O(log n) on sorted arrays
- **Bubble Sort**, **Selection Sort**, **Insertion Sort** — O(n²) foundational sorts

---

## 🛠️ Tech Stack

- **Language:** C# (.NET 10.0)
- **Paradigm:** Generic, strongly-typed implementations
- **Dependencies:** None (pure BCL)
- **Pattern:** Interface-based comparison via `Comparer<T>.Default`

---

## 🏗️ Architecture & Design Decisions

1. **Generic Type Parameters** — All structures are `<T>` generic, supporting any comparable type via `IComparer<T>`.

2. **Self-Balancing Rotation Logic** — AVL and Red-Black trees implement precise rotation sequences (LL, RR, LR, RL) to maintain O(log n) guaranteed performance.

3. **Adjacency Matrix for Graphs** — Chosen over adjacency lists for O(1) edge existence checks; supports both directed and undirected modes.

4. **Heap Internal Implementation** — Array-backed binary heap with implicit indexing, avoiding node allocation overhead.

5. **Two Dijkstra Variants** — The optimized version uses a custom `MinPriorityQueue` to demonstrate algorithmic improvement from O(V²) to O(E log V).

6. **Explicit Traversal Methods** — BFS (queue-based) and DFS (stack-based) exposed as first-class operations for trees and graphs.

---

## 🚦 Quick Start

```bash
# Clone and navigate to the project
cd advanced-data-structure-implementation-main/Advanced_DS

# Build
dotnet build

# Run
dotnet run
```

---

## 💡 Usage Examples

### AVL Tree

```csharp
var avl = new AVLTree<int>();
avl.Insert(10);
avl.Insert(20);
avl.Insert(30); // Triggers rotation automatically

avl.Exists(20); // True
avl.Delete(20);
```

### Graph with Dijkstra

```csharp
var vertices = new List<string> { "A", "B", "C", "D" };
var graph = new Graph<string>(vertices, Graph<string>.enGraphDirectionType.unDirected);

graph.AddEdge("A", "B", 4);
graph.AddEdge("A", "C", 2);
graph.AddEdge("B", "C", 1);
graph.AddEdge("B", "D", 5);
graph.AddEdge("C", "D", 8);

var shortestPaths = graph.EfficientDijkstra("A");
// Returns distance and path to all vertices
```

### Priority Queue

```csharp
var priorityQueue = new MaxPriorityQueue<int>();
priorityQueue.Insert(50);
priorityQueue.Insert(100);
priorityQueue.Insert(25);

priorityQueue.ExtractMax(); // Returns 100
priorityQueue.Peek();       // Returns 50 (if 100 was removed)
```

---

## 🎯 Key Strengths

- ✅ **Zero external dependencies** — Pure BCL, no NuGet packages required
- ✅ **Generic throughout** — Type-safe, reusable across any `IComparable<T>`
- ✅ **Self-balancing** — Guaranteed O(log n) performance for tree operations
- ✅ **Optimized algorithms** — Dijkstra with priority queue for large graphs
- ✅ **Complete operations** — Insert, delete, search, traverse all implemented
- ✅ **Educational + production-ready** — Clean code suitable for learning or integration

---

## 🔮 Future Improvements

- [ ] B-Tree / B+Tree for database-style indexing
- [ ] Trie (prefix tree) for autocomplete scenarios
- [ ] Segment Tree for range queries
- [ ] Union-Find / Disjoint Set with path compression
- [ ] A* pathfinding algorithm
- [ ] More sorting algorithms (QuickSort, MergeSort, HeapSort)
- [ ] Unit tests with xUnit/NUnit

---

## 📄 License

MIT License — Feel free to use, modify, and distribute.

---

> *Built with care, precision, and a genuine love for algorithms.* 🧠💚
