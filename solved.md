# LeetCode Solved Problems — Revision Sheet

**Total: 137**  |  Easy: 34  |  Medium: 90  |  Hard: 13

Each problem is filed under its most specific topic tag (rarest tag it carries).

**Jump to a topic:**

- [Tree (10)](#tree-10)
- [Dynamic Programming (9)](#dynamic-programming-9)
- [Backtracking (8)](#backtracking-8)
- [Binary Search (8)](#binary-search-8)
- [Greedy (8)](#greedy-8)
- [Matrix (7)](#matrix-7)
- [Database (5)](#database-5)
- [Monotonic Stack (5)](#monotonic-stack-5)
- [Recursion (5)](#recursion-5)
- [Sliding Window (5)](#sliding-window-5)
- [Design (4)](#design-4)
- [Linked List (4)](#linked-list-4)
- [Sorting (4)](#sorting-4)
- [String (4)](#string-4)
- [Trie (4)](#trie-4)
- [Two Pointers (4)](#two-pointers-4)
- [Union-Find (4)](#union-find-4)
- [Binary Search Tree (3)](#binary-search-tree-3)
- [Bit Manipulation (3)](#bit-manipulation-3)
- [Divide and Conquer (3)](#divide-and-conquer-3)
- [Math (3)](#math-3)
- [Array (2)](#array-2)
- [Breadth-First Search (2)](#breadth-first-search-2)
- [Prefix Sum (2)](#prefix-sum-2)
- [Stack (2)](#stack-2)
- [Topological Sort (2)](#topological-sort-2)
- [Bucket Sort (1)](#bucket-sort-1)
- [Combinatorics (1)](#combinatorics-1)
- [Counting (1)](#counting-1)
- [Data Stream (1)](#data-stream-1)
- [Doubly-Linked List (1)](#doubly-linked-list-1)
- [Enumeration (1)](#enumeration-1)
- [Geometry (1)](#geometry-1)
- [Graph Theory (1)](#graph-theory-1)
- [Hash Function (1)](#hash-function-1)
- [Hash Table (1)](#hash-table-1)
- [Heap (Priority Queue) (1)](#heap-priority-queue-1)
- [Merge Sort (1)](#merge-sort-1)
- [Number Theory (1)](#number-theory-1)
- [Queue (1)](#queue-1)
- [Quickselect (1)](#quickselect-1)
- [Simulation (1)](#simulation-1)
- [String Matching (1)](#string-matching-1)

## Tree (10)

### 🟢 100. Same Tree

**Easy** · 🏷️ Tree, Depth-First Search, Breadth-First Search, Binary Tree · 📅 2026-03-03

#### 📄 Problem

Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

 

Example 1:

```
**Input:** p = [1,2,3], q = [1,2,3]
**Output:** true
```

Example 2:

```
**Input:** p = [1,2], q = [1,null,2]
**Output:** false
```

Example 3:

```
**Input:** p = [1,2,1], q = [1,1,2]
**Output:** false
```

 

**Constraints:**

	- The number of nodes in both trees is in the range `[0, 100]`.
	- `-10^4 <= Node.val <= 10^4`

#### 💡 Revision note

```text
Pattern: Recursive DFS
Key idea: Recursively verify node values match and both subtrees are identical simultaneously, leveraging tree structure.
Complexity: O(min(m,n)) time / O(h) space where h is tree height
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {

        return checksame(p,q);
                
    }

    private boolean checksame(TreeNode p, TreeNode q){
        if(p == null && q == null){
            return true;
        }

        if(p==null && q!=null){
            return false;
        }
        if(p != null && q == null){
            return false;
        }
        return p.val == q.val && checksame(p.left,q.left) && checksame(p.right,q.right); 
    }
}
```

</details>

### 🟢 104. Maximum Depth of Binary Tree

**Easy** · 🏷️ Tree, Depth-First Search, Breadth-First Search, Binary Tree · 📅 2025-11-19

#### 📄 Problem

Given the `root` of a binary tree, return *its maximum depth*.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

 

Example 1:

```
**Input:** root = [3,9,20,null,null,15,7]
**Output:** 3
```

Example 2:

```
**Input:** root = [1,null,2]
**Output:** 2
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 10^4]`.
	- `-100 <= Node.val <= 100`

#### 💡 Revision note

```text
Pattern: DFS Recursion
Key idea: Maximum depth at each node equals 1 plus the maximum of its left and right subtree depths; recurse to all nodes.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int maxDepth(TreeNode root) {

        return height(root);
        
    }

    private int height(TreeNode root){
        if(root == null){
            return 0;
        }

        return Integer.max(height(root.left),height(root.right))+1;
    }
}
```

</details>

### 🟢 110. Balanced Binary Tree

**Easy** · 🏷️ Tree, Depth-First Search, Binary Tree · 📅 2026-03-02

#### 📄 Problem

Given a binary tree, determine if it is **height-balanced**.

 

Example 1:

```
**Input:** root = [3,9,20,null,null,15,7]
**Output:** true
```

Example 2:

```
**Input:** root = [1,2,2,3,3,null,null,4,4]
**Output:** false
```

Example 3:

```
**Input:** root = []
**Output:** true
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 5000]`.
	- `-10^4 <= Node.val <= 10^4`

#### 💡 Revision note

```text
Pattern: Recursive DFS
Key idea: A tree is balanced if each node's subtrees differ in height by ≤ 1 and are themselves balanced.
Complexity: O(n²) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isBalanced(TreeNode root) {
        int left = 0;
        int right = 0;
        if(root == null){
            return true;
        }
        if(root.left != null){
            left = height(root.left);
        }
        if(root.right != null){
            right = height(root.right);
        }

        boolean ischeck =  Math.abs(left-right)<=1 ;
        return ischeck && isBalanced(root.left) && isBalanced(root.right);
        
    }

    private int height(TreeNode root){
        if(root == null){
            return 0;
        }

        int left = 1 + height(root.left);
        int right = 1 + height(root.right);
        return Integer.max(left,right);
    }
}
```

</details>

### 🟢 226. Invert Binary Tree

**Easy** · 🏷️ Tree, Depth-First Search, Breadth-First Search, Binary Tree · 📅 2026-03-04

#### 📄 Problem

Given the `root` of a binary tree, invert the tree, and return *its root*.

 

Example 1:

```
**Input:** root = [4,2,7,1,3,6,9]
**Output:** [4,7,2,9,6,3,1]
```

Example 2:

```
**Input:** root = [2,1,3]
**Output:** [2,3,1]
```

Example 3:

```
**Input:** root = []
**Output:** []
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 100]`.
	- `-100 <= Node.val <= 100`

#### 💡 Revision note

```text
Pattern: Tree recursion
Key idea: Recursively swap left and right children at each node to mirror the tree structure.
Complexity: O(n) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode invertTree(TreeNode root) {

        return invert(root);
        
    }

    private TreeNode invert(TreeNode root){

        if(root == null){
            return null;
        }

        TreeNode left = invert(root.left);
        TreeNode right = invert(root.right);
        root.left = right;
        root.right = left;
        return root;
    }
}
```

</details>

### 🟢 543. Diameter of Binary Tree

**Easy** · 🏷️ Tree, Depth-First Search, Binary Tree · 📅 2026-03-01

#### 📄 Problem

Given the `root` of a binary tree, return *the length of the **diameter** of the tree*.

The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.

 

Example 1:

```
**Input:** root = [1,2,3,4,5]
**Output:** 3
**Explanation:** 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```

Example 2:

```
**Input:** root = [1,2]
**Output:** 1
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[1, 10^4]`.
	- `-100 <= Node.val <= 100`

#### 💡 Revision note

```text
Pattern: DFS with height calculation
Key idea: Maximum diameter at each node is the sum of its subtrees' heights; track the global maximum.
Complexity: O(n) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int max = 0;
    public int diameterOfBinaryTree(TreeNode root) {
         height(root);
         return max;
    }

    private int height(TreeNode root){
        if(root == null){
            return 0;
        }

        int left =  height(root.left);
        int right = height(root.right);
        max = Integer.max(max,left+right);

        return 1 + Integer.max(left,right);
    }
}
```

</details>

### 🟡 102. Binary Tree Level Order Traversal

**Medium** · 🏷️ Tree, Breadth-First Search, Binary Tree · 📅 2025-11-22

#### 📄 Problem

Given the `root` of a binary tree, return *the level order traversal of its nodes' values*. (i.e., from left to right, level by level).

 

Example 1:

```
**Input:** root = [3,9,20,null,null,15,7]
**Output:** [[3],[9,20],[15,7]]
```

Example 2:

```
**Input:** root = [1]
**Output:** [[1]]
```

Example 3:

```
**Input:** root = []
**Output:** []
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 2000]`.
	- `-1000 <= Node.val <= 1000`

#### 💡 Revision note

```text
Pattern: Queue-based BFS
Key idea: Capture queue size at each iteration to identify and process all current-level nodes.
Complexity: O(n) time / O(w) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> res = new ArrayList<>();

        Queue<TreeNode> q = new LinkedList<>();
        
        if(root!=null){
            q.add(root);
        }
            
        while(!q.isEmpty()){
            List<Integer> nested = new ArrayList<>();
            int level = q.size();

            for(int i = 0;i<level;i++){
                TreeNode node =  q.poll();
                nested.add(node.val);
                if(node.left != null){
                    q.offer(node.left);
                }
                if(node.right != null){
                    q.offer(node.right);
                }
            }
            res.add(nested);
            level++;
            
        }

        return res;

    }
}
```

</details>

### 🟡 199. Binary Tree Right Side View

**Medium** · 🏷️ Tree, Depth-First Search, Breadth-First Search, Binary Tree · 📅 2025-11-22

#### 📄 Problem

Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return *the values of the nodes you can see ordered from top to bottom*.

 

Example 1:

**Input:** root = [1,2,3,null,5,null,4]

**Output:** [1,3,4]

**Explanation:**

Example 2:

**Input:** root = [1,2,3,4,null,null,null,5]

**Output:** [1,3,4,5]

**Explanation:**

Example 3:

**Input:** root = [1,null,3]

**Output:** [1,3]

Example 4:

**Input:** root = []

**Output:** []

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 100]`.
	- `-100 <= Node.val <= 100`

#### 💡 Revision note

```text
Level-order BFS
Level-order BFS traverses left-to-right per level; the rightmost visible node is the last one at each depth.
O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> rightSideView(TreeNode root) {

        List<List<Integer>> levelOrderTraversal = levelOrderTraversal(root);
        List<Integer> res = new ArrayList<>();
        for(List<Integer> list : levelOrderTraversal){
            res.add(list.get(list.size()-1));
        }
        return res;
        
    }

    private List<List<Integer>> levelOrderTraversal(TreeNode root){

        Queue<TreeNode> q = new LinkedList<>();
        List<List<Integer>> res = new ArrayList<>();

        if(root != null){
            q.offer(root);
        }

        while(!q.isEmpty()){
            int size = q.size();
            List<Integer> list = new ArrayList<>();

            for(int i = 0;i<size ;i++ ){
                TreeNode node = q.poll();
                list.add(node.val);
                if(node.left != null){
                    q.offer(node.left);
                }
                if(node.right != null){
                    q.offer(node.right);
                }
            }
            res.add(list);
        }



        return res;

    }
}

```

</details>

### 🟡 236. Lowest Common Ancestor of a Binary Tree

**Medium** · 🏷️ Tree, Depth-First Search, Binary Tree · 📅 2026-03-02

#### 📄 Problem

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

 

Example 1:

```
**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
**Output:** 3
**Explanation:** The LCA of nodes 5 and 1 is 3.
```

Example 2:

```
**Input:** root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
**Output:** 5
**Explanation:** The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```

Example 3:

```
**Input:** root = [1,2], p = 1, q = 2
**Output:** 1
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[2, 10^5]`.
	- `-10^9 <= Node.val <= 10^9`
	- All `Node.val` are **unique**.
	- `p != q`
	- `p` and `q` will exist in the tree.

#### 💡 Revision note

```text
Pattern: Divide and conquer
Key idea: When p and q are in different subtrees, current node is LCA; otherwise find LCA in subtree containing both.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {

        return LCA(root,p.val,q.val);
        
    }

    private TreeNode LCA(TreeNode root, int p, int q){

        if(root == null){
            return null;
        }

        if(root.val == p || root.val == q){
            return root;
        }

        TreeNode left = LCA(root.left,p,q);
        TreeNode right = LCA(root.right,p,q);

        if(left != null && right != null){
            return root;
        }
        if(left != null){
            return left;
        }

        return right;


    }
}
```

</details>

### 🟡 1448. Count Good Nodes in Binary Tree

**Medium** · 🏷️ Tree, Depth-First Search, Breadth-First Search, Binary Tree · 📅 2026-03-05

#### 📄 Problem

Given a binary tree `root`, a node *X* in the tree is named **good** if in the path from root to *X* there are no nodes with a value *greater than* X.



Return the number of **good** nodes in the binary tree.



 


Example 1:



****




```
**Input:** root = [3,1,4,3,null,1,5]
**Output:** 4
**Explanation:** Nodes in blue are **good**.
Root Node (3) is always a good node.
Node 4 -> (3,4) is the maximum value in the path starting from the root.
Node 5 -> (3,4,5) is the maximum value in the path
Node 3 -> (3,1,3) is the maximum value in the path.
```


Example 2:



****




```
**Input:** root = [3,3,null,4,2]
**Output:** 3
**Explanation:** Node 2 -> (3, 3, 2) is not good, because "3" is higher than it.
```


Example 3:




```
**Input:** root = [1]
**Output:** 1
**Explanation:** Root is considered as **good**.
```


 


**Constraints:**





	- The number of nodes in the binary tree is in the range `[1, 10^5]`.
	- Each node's value is between `[-10^4, 10^4]`.

#### 💡 Revision note

```text
Pattern: DFS with path max
Key idea: A node is good if its value ≥ the maximum value seen on the path from root.
Complexity: O(n) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int max = 1;
    public int goodNodes(TreeNode root) {
        return dfs(root,root.val);
    }

    private int dfs(TreeNode root, int maxSoFar){

        if(root == null){
            return 0;
        }

        int c = 0;
        if(root.val>=maxSoFar){
            c=1;
        }
        maxSoFar = Integer.max(maxSoFar,root.val);

        c=c+dfs(root.left,maxSoFar);
        c=c+dfs(root.right,maxSoFar);

        return c;

        
    }
}
```

</details>

### 🔴 124. Binary Tree Maximum Path Sum

**Hard** · 🏷️ Dynamic Programming, Tree, Depth-First Search, Binary Tree · 📅 2025-11-28

#### 📄 Problem

A **path** in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence **at most once**. Note that the path does not need to pass through the root.

The **path sum** of a path is the sum of the node's values in the path.

Given the `root` of a binary tree, return *the maximum **path sum** of any **non-empty** path*.

 

Example 1:

```
**Input:** root = [1,2,3]
**Output:** 6
**Explanation:** The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.
```

Example 2:

```
**Input:** root = [-10,9,20,null,null,15,7]
**Output:** 42
**Explanation:** The optimal path is 15 -> 20 -> 7 with a path sum of 15 + 20 + 7 = 42.
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[1, 3 * 10^4]`.
	- `-1000 <= Node.val <= 1000`

#### 💡 Revision note

```text
Pattern: Tree path DP
Key idea: Compute maximum path through each node by merging subtrees for the global answer, but return only the best single branch upward.
Complexity: O(n) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int ans = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {

         dfs(root);
         return ans;
        
    }

    private int dfs(TreeNode root){
        if(root == null){
            return 0;
        }

        int left = Integer.max(0,dfs(root.left));
        int right = Integer.max(0,dfs(root.right));

        int currSumBoth = root.val +left+right;

        ans = Integer.max(ans,currSumBoth);

        return root.val + Integer.max(left,right);


    }
}
```

</details>

---

## Dynamic Programming (9)

### 🟢 121. Best Time to Buy and Sell Stock

**Easy** · 🏷️ Array, Dynamic Programming · 📅 2026-07-11

#### 📄 Problem

You are given an array `prices` where `prices[i]` is the price of a given stock on the `i^th` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return *the maximum profit you can achieve from this transaction*. If you cannot achieve any profit, return `0`.

 

Example 1:

```
**Input:** prices = [7,1,5,3,6,4]
**Output:** 5
**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

Example 2:

```
**Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** In this case, no transactions are done and the max profit = 0.
```

 

**Constraints:**

	- `1 <= prices.length <= 10^5`
	- `0 <= prices[i] <= 10^4`

#### 💡 Revision note

```text
Pattern: Single-pass min tracking
Key idea: Maximum profit at each price is current price minus the minimum price before it.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxProfit(int[] arr) {

        int n = arr.length;
        int min = arr[0];
        int ans =0;

        for(int i = 1;i<n;i++){
            min = Integer.min(arr[i],min);
            ans = Integer.max(ans, arr[i]-min);
        }

        return ans;
        

    }

    

  
}
```

</details>

### 🟡 72. Edit Distance

**Medium** · 🏷️ String, Dynamic Programming · 📅 2026-01-13

#### 📄 Problem

Given two strings `word1` and `word2`, return *the minimum number of operations required to convert `word1` to `word2`*.

You have the following three operations permitted on a word:

	- Insert a character
	- Delete a character
	- Replace a character

 

Example 1:

```
**Input:** word1 = "horse", word2 = "ros"
**Output:** 3
**Explanation:** 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

Example 2:

```
**Input:** word1 = "intention", word2 = "execution"
**Output:** 5
**Explanation:** 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

 

**Constraints:**

	- `0 <= word1.length, word2.length <= 500`
	- `word1` and `word2` consist of lowercase English letters.

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: When characters match, no operation needed; when they don't, choose minimum cost among insert, delete, or replace operations.
Complexity: O(n*m) time / O(n*m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minDistance(String word1, String word2) {

        int n = word1.length();
        int m = word2.length();
        int[][] dp = new int[n][m];
        for(int i = 0;i<n;i++){
            Arrays.fill(dp[i],-1);
        }

        return findmin(n-1,m-1,word1,word2,dp);

        
    }

    private int findmin(int i, int j, String w1, String w2, int[][] dp){

        if(i < 0){
            return j+1;
        }

        if(j < 0){
           return i+1;
        }
        if(dp[i][j] != -1){
            return dp[i][j];
        }
        

        if(w1.charAt(i) == w2.charAt(j)){
            return dp[i][j]=findmin(i-1,j-1,w1,w2,dp);
        }
        int replace = 1 + findmin(i-1,j-1,w1,w2,dp);
        int remove = 1 + findmin(i-1,j,w1,w2,dp);
        int insert = 1 + findmin(i,j-1,w1,w2,dp);
        return dp[i][j]=Integer.min(insert, Integer.min(replace,remove));

    }
}
```

</details>

### 🟡 120. Triangle

**Medium** · 🏷️ Array, Dynamic Programming · 📅 2025-12-30

#### 📄 Problem

Given a `triangle` array, return *the minimum path sum from top to bottom*.

For each step, you may move to an adjacent number of the row below. More formally, if you are on index `i` on the current row, you may move to either index `i` or index `i + 1` on the next row.

 

Example 1:

```
**Input:** triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]
**Output:** 11
**Explanation:** The triangle looks like:
   2
  3 4
 6 5 7
4 1 8 3
The minimum path sum from top to bottom is 2 + 3 + 5 + 1 = 11 (underlined above).
```

Example 2:

```
**Input:** triangle = [[-10]]
**Output:** -10
```

 

**Constraints:**

	- `1 <= triangle.length <= 200`
	- `triangle[0].length == 1`
	- `triangle[i].length == triangle[i - 1].length + 1`
	- `-10^4 <= triangle[i][j] <= 10^4`

 

**Follow up:** Could you do this using only `O(n)` extra space, where `n` is the total number of rows in the triangle?

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: At each position, minimum path equals current value plus the minimum of two paths below; memoize to avoid recomputation.
Complexity: O(n²) time / O(n²) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minimumTotal(List<List<Integer>> triangle) {
        int n = triangle.size();
        int m = triangle.get(n-1).size();
        int[][] dp = new int[n][m];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],(int)1e9);
        }
        return findmin(0,0,triangle.size(),triangle,dp);
        
    }

    private int findmin(int i, int j ,int n, List<List<Integer>> triangle,int[][] dp){
        if(i == n-1){
            return triangle.get(i).get(j);
        }
        if(dp[i][j]!=(int)1e9){
            return dp[i][j];
        }

        int d = triangle.get(i).get(j) + findmin(i+1,j,n,triangle,dp);
        int da = triangle.get(i).get(j) + findmin(i+1,j+1,n,triangle,dp);
        return dp[i][j]=Integer.min(d,da);
    }
}
```

</details>

### 🟡 152. Maximum Product Subarray

**Medium** · 🏷️ Array, Dynamic Programming · 📅 2026-02-02

#### 📄 Problem

Given an integer array `nums`, find a subarray that has the largest product, and return *the product*.

The test cases are generated so that the answer will fit in a **32-bit** integer.

**Note** that the product of an array with a single element is the value of that element.

 

Example 1:

```
**Input:** nums = [2,3,-2,4]
**Output:** 6
**Explanation:** [2,3] has the largest product 6.
```

Example 2:

```
**Input:** nums = [-2,0,-1]
**Output:** 0
**Explanation:** The result cannot be 2, because [-2,-1] is not a subarray.
```

 

**Constraints:**

	- `1 <= nums.length <= 2 * 10^4`
	- `-10 <= nums[i] <= 10`
	- The product of any subarray of `nums` is **guaranteed** to fit in a **32-bit** integer.

#### 💡 Revision note

```text
Pattern: Prefix-Suffix Product Scan
Key idea: Products from both left and right cover all subarrays; resetting at zeros handles negative-caused sign flips naturally.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        // if(n==1){
        //     return nums[0];
        // }
        return findmax(nums.length,nums);
        
    }

    private int findmax(int n , int[] arr){

        int pre = 1;
        int suf = 1;
        int ans = Integer.MIN_VALUE;

        for(int i=0; i<n; i++){
            if(pre == 0){
                pre = 1;
            }
            if(suf == 0){
                suf = 1;
            }
            pre = pre * arr[i];
            suf = suf * arr[n-i-1];
            
            ans = Integer.max(ans,Integer.max(pre,suf));
            System.out.println(ans);
        }

        return ans;
    }
}
```

</details>

### 🟡 198. House Robber

**Medium** · 🏷️ Array, Dynamic Programming · 📅 2025-12-25

#### 📄 Problem

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return *the maximum amount of money you can rob tonight **without alerting the police***.

 

Example 1:

```
**Input:** nums = [1,2,3,1]
**Output:** 4
**Explanation:** Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

Example 2:

```
**Input:** nums = [2,7,9,3,1]
**Output:** 12
**Explanation:** Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.
```

 

**Constraints:**

	- `1 <= nums.length <= 100`
	- `0 <= nums[i] <= 400`

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Two choices per house—rob (add to i-2 max) or skip (keep i-1 max)—pick maximum; memoize subproblems.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int rob(int[] nums) {

        int n = nums.length;
        if(n==1){
            return nums[0];
        }
        int[] dp = new int[n];
        Arrays.fill(dp,-1);
        getmax(n-1,dp,nums);
        return dp[n-1];
        
    }

    private int getmax(int i, int[] dp, int[] arr){

        if(i == 0 ){
            return arr[i];
        }
        if(i<0){
            return 0;
        }

        if(dp[i]!=-1){
            return dp[i];
        }

        int pick = getmax(i-2, dp, arr) + arr[i];

        int notpick = getmax(i-1,dp,arr);

        return dp[i]=Integer.max(pick,notpick);
    }
}
```

</details>

### 🟡 213. House Robber II

**Medium** · 🏷️ Array, Dynamic Programming · 📅 2026-01-18

#### 📄 Problem

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are **arranged in a circle.** That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return *the maximum amount of money you can rob tonight **without alerting the police***.

 

Example 1:

```
**Input:** nums = [2,3,2]
**Output:** 3
**Explanation:** You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
```

Example 2:

```
**Input:** nums = [1,2,3,1]
**Output:** 4
**Explanation:** Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
```

Example 3:

```
**Input:** nums = [1,2,3]
**Output:** 3
```

 

**Constraints:**

	- `1 <= nums.length <= 100`
	- `0 <= nums[i] <= 1000`

#### 💡 Revision note

```text
Pattern: Case-split DP
Key idea: Circular constraint prevents robbing both endpoints; solve two linear subproblems (exclude first or last) and take maximum.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        if(n==1){
            return nums[0];
        }
        int[] arr1 = new int[n-1];
        int[] arr2 = new int[n-1];

        for(int i = 0; i<n-1; i++){
           arr1[i]=nums[i];
        }
        for(int i = 1;i<n;i++){
            arr2[i-1]=nums[i];
        }
        int[] dp1 = new int[n-1];
        int[] dp2 = new int[n-1];

        Arrays.fill(dp1,-1);
        Arrays.fill(dp2,-1);

        int m1 =  findmax(n-2,arr1,dp1);
        int m2 =  findmax(n-2,arr2,dp2);
        return Integer.max(m1,m2);
        

        
    }

    private int findmax(int i, int[] arr,int[] dp){
        if(i == 0){
           return arr[0];
        }
        if(i<0){
            return 0;
        }
        if(dp[i]!=-1){
            return dp[i];
        }
        int nonpick = findmax(i-1,arr,dp);
        int pick = arr[i] + findmax(i-2,arr,dp);
        
        return  dp[i]=Integer.max(pick,nonpick);
    }

}
```

</details>

### 🟡 518. Coin Change II

**Medium** · 🏷️ Array, Dynamic Programming · 📅 2026-01-05

#### 📄 Problem

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return *the number of combinations that make up that amount*. If that amount of money cannot be made up by any combination of the coins, return `0`.

You may assume that you have an infinite number of each kind of coin.

The **final** answer is **guaranteed** to fit into a signed **32-bit** integer.

 

Example 1:

```
**Input:** amount = 5, coins = [1,2,5]
**Output:** 4
**Explanation:** there are four ways to make up the amount:
5=5
5=2+2+1
5=2+1+1+1
5=1+1+1+1+1
```

Example 2:

```
**Input:** amount = 3, coins = [2]
**Output:** 0
**Explanation:** the amount of 3 cannot be made up just with coins of 2.
```

Example 3:

```
**Input:** amount = 10, coins = [10]
**Output:** 1
```

 

**Constraints:**

	- `1 <= coins.length <= 300`
	- `1 <= coins[i] <= 5000`
	- All the values of `coins` are **unique**.
	- `0 <= amount <= 5000`

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: Iterate coins sequentially, keeping index fixed when picking to allow reuse and count combinations not permutations.
Complexity: O(n × amount) time / O(n × amount) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int change( int amount,int[] coins) {

        int n = coins.length;
        int[][] dp = new int[n][amount+1];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],-1);
        }
        return findmin(n-1,coins,amount,dp);
        
    }

    private int findmin(int i, int[] arr, int t,int[][] dp){

        if(i == 0){
            return (t % arr[i]) == 0 ? 1 : 0;
        }
        if(dp[i][t]!=-1){
            return dp[i][t];
        }
        int nonpick =   findmin(i-1, arr, t,dp);
        int pick =  0;
        if(arr[i]<=t){
            pick =  findmin(i, arr, t-arr[i],dp);
        }
        return dp[i][t]=pick+nonpick;
    }
}
```

</details>

### 🟡 1143. Longest Common Subsequence

**Medium** · 🏷️ String, Dynamic Programming · 📅 2026-01-06

#### 📄 Problem

Given two strings `text1` and `text2`, return *the length of their longest **common subsequence**. *If there is no **common subsequence**, return `0`.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

	- For example, `"ace"` is a subsequence of `"abcde"`.

A **common subsequence** of two strings is a subsequence that is common to both strings.

 

Example 1:

```
**Input:** text1 = "abcde", text2 = "ace" 
**Output:** 3  
**Explanation:** The longest common subsequence is "ace" and its length is 3.
```

Example 2:

```
**Input:** text1 = "abc", text2 = "abc"
**Output:** 3
**Explanation:** The longest common subsequence is "abc" and its length is 3.
```

Example 3:

```
**Input:** text1 = "abc", text2 = "def"
**Output:** 0
**Explanation:** There is no such common subsequence, so the result is 0.
```

 

**Constraints:**

	- `1 <= text1.length, text2.length <= 1000`
	- `text1` and `text2` consist of only lowercase English characters.

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Matching characters extend LCS by 1; mismatches require excluding one—recursively try both and take maximum.
Complexity: O(n*m) time / O(n*m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int n = text1.length();
        int m = text2.length();
        int[][] dp = new int[n+1][m+1];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],-1);
        }
        return findsubseq(n-1,m-1,text1,text2,dp);
        
    }

    private int findsubseq(int i ,  int j , String text1, String text2,int[][] dp){

        if(i<0 || j<0){
            return 0;
        }

        if(dp[i][j]!=-1){
            return dp[i][j];
        }
        if(text1.charAt(i) == text2.charAt(j)){
            return dp[i][j]= 1 + findsubseq(i-1,j-1,text1,text2, dp);
        }

        return dp[i][j]=Integer.max(findsubseq(i-1,j,text1,text2,dp),findsubseq(i,j-1,text1,text2,dp));
    }
}
```

</details>

### 🔴 115. Distinct Subsequences

**Hard** · 🏷️ String, Dynamic Programming · 📅 2026-01-11

#### 📄 Problem

Given two strings s and t, return *the number of distinct* ***subsequences**** of *s* which equals *t.

The test cases are generated so that the answer fits on a 32-bit signed integer.

 

Example 1:

```
**Input:** s = "rabbbit", t = "rabbit"
**Output:** 3
**Explanation:**
As shown below, there are 3 ways you can generate "rabbit" from s.
`**rabb**b**it**`
`**ra**b**bbit**`
`**rab**b**bit**`
```

Example 2:

```
**Input:** s = "babgbag", t = "bag"
**Output:** 5
**Explanation:**
As shown below, there are 5 ways you can generate "bag" from s.
`**ba**b**g**bag`
`**ba**bgba**g**`
`**b**abgb**ag**`
`ba**b**gb**ag**`
`babg**bag**`
```

 

**Constraints:**

	- `1 <= s.length, t.length <= 1000`
	- `s` and `t` consist of English letters.

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: For each position, if characters match, count both using and skipping; if not, skip.
Complexity: O(n*m) time / O(n*m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int numDistinct(String s, String t) {

        int n = s.length();
        int m = t.length();

        int[][] dp = new int[n][m];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],-1);
        }
        
        return findcount(n-1,m-1,s,t,dp);
    }

    private int findcount(int i, int j , String s, String t,int[][] dp){

        if(j<0){
            return 1;
        }
        if(i<0){
            return 0;
        }
        if(dp[i][j]!=-1){
            return dp[i][j];
        }

        if(s.charAt(i) == t.charAt(j)){
            return dp[i][j]=findcount(i-1,j-1,s,t,dp) + findcount(i-1,j,s,t,dp);

        }
        return dp[i][j]=findcount(i-1,j,s,t,dp);
    }
}
```

</details>

---

## Backtracking (8)

### 🟡 17. Letter Combinations of a Phone Number

**Medium** · 🏷️ Hash Table, String, Backtracking · 📅 2025-12-14

#### 📄 Problem

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

 

Example 1:

```
**Input:** digits = "23"
**Output:** ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

Example 2:

```
**Input:** digits = "2"
**Output:** ["a","b","c"]
```

 

**Constraints:**

	- `1 <= digits.length <= 4`
	- `digits[i]` is a digit in the range `['2', '9']`.

#### 💡 Revision note

```text
Pattern: Backtracking
Key idea: Recursively choose one letter per digit to explore all possible combinations.
Complexity: O(4^n * n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<String> letterCombinations(String digits) {
        Map<Integer,String> map = Map.of(
            2, "abc",
            3, "def",
            4, "ghi",
            5, "jkl",
            6, "mno",
            7, "pqrs",
            8, "tuv",
            9, "wxyz"
        );
        List<String> list = new ArrayList<>();
        numbers(digits,0,"",digits.length(),map,list);
        return list;

    }

    private void numbers(String digits, int idx, String str,int n, Map<Integer,String> map, List<String> list){

        if(idx == n){
            list.add(str);
            return;
        }


        int val = Integer.valueOf(digits.charAt(idx)) - 48 ;
        String s = map.get(val);

        for(int i = 0; i<s.length(); i++){
            numbers(digits, idx+1, str + s.charAt(i), n, map, list);
        }
    }
}
```

</details>

### 🟡 22. Generate Parentheses

**Medium** · 🏷️ String, Dynamic Programming, Backtracking · 📅 2025-12-13

#### 📄 Problem

Given `n` pairs of parentheses, write a function to *generate all combinations of well-formed parentheses*.

 

Example 1:

```
**Input:** n = 3
**Output:** ["((()))","(()())","(())()","()(())","()()()"]
```
Example 2:

```
**Input:** n = 1
**Output:** ["()"]
```

 

**Constraints:**

	- `1 <= n <= 8`

#### 💡 Revision note

```text
Pattern: Backtracking
Key idea: Place ')' only when open count > close count—this simple constraint ensures all generated sequences are valid.
Complexity: O(4^n / √n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> list = new ArrayList<>();
        generate(0,0,"",n,list);
        return list;
        
    }

    private void generate(int open, int close,String s, int n,List<String> list){

        if(n*2 == s.length()){
            list.add(s);
            return;
        }

        if(open<n){
            generate(open+1,close,s+"(",n,list);
        }
        if(close<open){
            generate(open,close+1,s+")",n,list);
        }
    }
}
```

</details>

### 🟡 39. Combination Sum

**Medium** · 🏷️ Array, Backtracking · 📅 2025-12-08

#### 📄 Problem

Given an array of **distinct** integers `candidates` and a target integer `target`, return *a list of all **unique combinations** of *`candidates`* where the chosen numbers sum to *`target`*.* You may return the combinations in **any order**.

The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.

 

Example 1:

```
**Input:** candidates = [2,3,6,7], target = 7
**Output:** [[2,2,3],[7]]
**Explanation:**
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
```

Example 2:

```
**Input:** candidates = [2,3,5], target = 8
**Output:** [[2,2,2,2],[2,3,3],[3,5]]
```

Example 3:

```
**Input:** candidates = [2], target = 1
**Output:** []
```

 

**Constraints:**

	- `1 <= candidates.length <= 30`
	- `2 <= candidates[i] <= 40`
	- All elements of `candidates` are **distinct**.
	- `1 <= target <= 40`

#### 💡 Revision note

```text
Pattern: Backtracking
Key idea: Include current candidate (same index allows reuse) or exclude (next index prevents duplicates).
Complexity: O(2^(T/M)) time / O(T/M) space, where T=target, M=min value
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {

        List<Integer> list = new ArrayList<>();
        List<List<Integer>> res = new ArrayList<>();
        comb(candidates,res,list,0,target,candidates.length);
        return res;
        
    }

    private void comb(int[] nums, List<List<Integer>> res, List<Integer> list , int i, int t,int n){

        if(t==0){
            res.add(new ArrayList<>(list));
            return;
        }

        if(t<0 || i>=n){
            return;
        }

        list.add(nums[i]);
        //single include
        comb(nums, res, list,i,t-nums[i],n);
        // exclude
        list.remove(list.size()-1);
        comb(nums,res,list,i+1,t,n);


    }
}
```

</details>

### 🟡 40. Combination Sum II

**Medium** · 🏷️ Array, Backtracking · 📅 2025-12-09

#### 📄 Problem

Given a collection of candidate numbers (`candidates`) and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sum to `target`.

Each number in `candidates` may only be used **once** in the combination.

**Note:** The solution set must not contain duplicate combinations.

 

Example 1:

```
**Input:** candidates = [10,1,2,7,6,1,5], target = 8
**Output:** 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

Example 2:

```
**Input:** candidates = [2,5,2,1,2], target = 5
**Output:** 
[
[1,2,2],
[5]
]
```

 

**Constraints:**

	- `1 <= candidates.length <= 100`
	- `1 <= candidates[i] <= 50`
	- `1 <= target <= 30`

#### 💡 Revision note

```text
Pattern: Backtracking with deduplication
Key idea: Sorting groups equal values; skipping duplicates during recursion prevents generating identical combinations.
Complexity: O(2^n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {

    Arrays.sort(candidates);
    List<List<Integer>> res = new ArrayList<>();
    List<Integer> list = new ArrayList<>();

    Set<List<Integer>> set = new HashSet<>();


        comb(candidates, res,list,0,target,candidates.length, set);
        return res;
        
    }


    private void comb(int[] arr, List<List<Integer>> res, List<Integer> list, int i, int t, int n, Set<List<Integer>> set){

        if(t == 0){
            Collections.sort(list);
            if(!set.contains(list)){
                res.add(new ArrayList<>(list));
                set.add(list);
            }
            return;
        }

        if(t<0 || i >= n){
            return ;
        }
        list.add(arr[i]);
        comb(arr,res,list,i+1,t-arr[i],n,set);
        list.remove(list.size()-1);
        while(i<n-1 && arr[i]==arr[i+1]){
            i++;
        }
        comb(arr,res,list,i+1,t,n,set);
    }
}
```

</details>

### 🟡 46. Permutations

**Medium** · 🏷️ Array, Backtracking · 📅 2025-12-11

#### 📄 Problem

Given an array `nums` of distinct integers, return all the possible permutations. You can return the answer in **any order**.

 

Example 1:

```
**Input:** nums = [1,2,3]
**Output:** [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```
Example 2:

```
**Input:** nums = [0,1]
**Output:** [[0,1],[1,0]]
```
Example 3:

```
**Input:** nums = [1]
**Output:** [[1]]
```

 

**Constraints:**

	- `1 <= nums.length <= 6`
	- `-10 <= nums[i] <= 10`
	- All the integers of `nums` are **unique**.

#### 💡 Revision note

```text
Pattern: Backtracking with swap
Key idea: Place each element at the current position and recursively permute the rest; backtrack to explore all possibilities.
Complexity: O(n! * n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {

        List<List<Integer>> res = new ArrayList<>();
        getPermutation(nums,0,nums.length,res);
        return res;
       
    }

    private void getPermutation(int[] nums , int idx, int n , List<List<Integer>> res){

        if(idx == n){
            res.add(Arrays.stream(nums).boxed().collect(Collectors.toList()));
            return;
        }

        for(int i = idx ;i<n;i++){
            swap(i,idx,nums);
            getPermutation(nums,idx+1,n,res);
            swap(i,idx,nums);
        }
    }

    private void swap(int i , int idx, int[] nums){
        int temp = nums[i];
        nums[i]=nums[idx];
        nums[idx]=temp;
    }
}
```

</details>

### 🟡 79. Word Search

**Medium** · 🏷️ Array, String, Backtracking, Depth-First Search, Matrix · 📅 2025-12-15

#### 📄 Problem

Given an `m x n` grid of characters `board` and a string `word`, return `true` *if* `word` *exists in the grid*.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

 

Example 1:

```
**Input:** board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
**Output:** true
```

Example 2:

```
**Input:** board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
**Output:** true
```

Example 3:

```
**Input:** board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
**Output:** false
```

 

**Constraints:**

	- `m == board.length`
	- `n = board[i].length`
	- `1 <= m, n <= 6`
	- `1 <= word.length <= 15`
	- `board` and `word` consists of only lowercase and uppercase English letters.

 

**Follow up:** Could you use search pruning to make your solution faster with a larger `board`?

#### 💡 Revision note

```text
Pattern: Backtracking DFS
Key idea: Mark visited cells during path exploration to prevent reuse within a path; unmark when backtracking to explore alternatives.
Complexity: O(m*n * 4^L) time / O(m*n + L) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

        int[] rr = {0,0,-1,1};
        int[] cc = {-1,1,0,0};

    public boolean exist(char[][] board, String word) {

        int n = board.length;
        int m = board[0].length;
        boolean[][] vis = new boolean[n][m];
        boolean res = false;

        for(int i =0;i<n;i++){
            for(int j = 0;j<m ;j++){
                if (board[i][j] == word.charAt(0)) {
                    res = res || findWord(i, j, 0, word, vis,board,n,m);
                    if(res)
                        return true;
                }
            }
           
        }
        return false;
        
    }

    private boolean findWord(int i ,int j, int s, String word , boolean[][] vis,char[][] board,int n, int m){

        if(s == word.length()){
            return true;
        }
        boolean res = false;

        if(i < 0 || i>= n || j<0 || j>=m || vis[i][j] || word.charAt(s) != board[i][j]){
            return false;
        }

        
        vis[i][j]= true;

        for(int k = 0 ;k<4 ;k++){
            int idx = i + rr[k];
            int idy = j + cc[k];
            res = res || findWord(idx,idy,s + 1,word,vis,board,n,m);     
        }
        vis[i][j]= false;
        
        return res;

    }
}
```

</details>

### 🟡 131. Palindrome Partitioning

**Medium** · 🏷️ String, Dynamic Programming, Backtracking · 📅 2025-12-14

#### 📄 Problem

Given a string `s`, partition `s` such that every substring of the partition is a **palindrome**. Return *all possible palindrome partitioning of *`s`.

 

Example 1:

```
**Input:** s = "aab"
**Output:** [["a","a","b"],["aa","b"]]
```
Example 2:

```
**Input:** s = "a"
**Output:** [["a"]]
```

 

**Constraints:**

	- `1 <= s.length <= 16`
	- `s` contains only lowercase English letters.

#### 💡 Revision note

```text
Pattern: Backtracking
Key idea: At each step, try all palindromic prefixes, recursively solve the rest, backtrack to explore all valid partitions.
Complexity: O(N * 2^N) time / O(N) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<String>> partition(String s) {

        List<List<String>> res = new ArrayList<>();
        List<String> list = new ArrayList<>();
        getSubsets(0,s,s.length(),list,res);

        return res;
    }

    private void getSubsets(int idx,  String s, int n,List<String> list,List<List<String>> res){

        if(idx == n){
            res.add(new ArrayList<>(list));
            return;
        }

        for(int i = idx ; i<n ; i++){
            if (isPalindrome(s, idx, i)) {
                list.add(s.substring(idx, i + 1));   // choose
                getSubsets(i + 1, s,n, list, res);       // explore
                list.remove(list.size() - 1);         // unchoose (backtrack)
            } 
        }

    }

    private boolean isPalindrome(String s, int l, int r) {
        while (l < r) {
            if (s.charAt(l) != s.charAt(r)) 
                return false;
            l++;
            r--;
        }
        return true;
    }
}
```

</details>

### 🔴 51. N-Queens

**Hard** · 🏷️ Array, Backtracking · 📅 2026-03-14

#### 📄 Problem

The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return *all distinct solutions to the **n-queens puzzle***. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

 

Example 1:

```
**Input:** n = 4
**Output:** [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
**Explanation:** There exist two distinct solutions to the 4-queens puzzle as shown above
```

Example 2:

```
**Input:** n = 1
**Output:** [["Q"]]
```

 

**Constraints:**

	- `1 <= n <= 9`

#### 💡 Revision note

```text
Pattern: Backtracking with constraint validation
Key idea: Early constraint validation prunes invalid branches exponentially, avoiding redundant exploration of impossible placements.
Complexity: O(N! * N) time / O(N) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<String>> solveNQueens(int n) {

        List<List<String>> board = new ArrayList<>();
        List<String> row = new ArrayList<>();   
        for(int i = 0;i<n ;i++){
            row.add(".".repeat(n));
        }

        placeQueens(0,n,row,board);
        return board;
        
    }


    private boolean isSafe(int row, int col, List<String> list,int n ){

        //for row
        if(list.get(row).contains("Q"))
            return false;
        
        //for column 
        for(int i = 0;i<n ;i++){
            char[] ch = list.get(i).toCharArray();
            if(ch[col] == 'Q'){
                return false;
            }
        }

        //left diagnol

        for(int i = row,j=col; i>=0 && j>=0 ; i--,j--){
            char[] ch = list.get(i).toCharArray();
            if(ch[j]=='Q'){
                return false;
            }
        }

        //right diagnol

        for(int i = row,j=col; i>=0 && j<n ; i--,j++){
            char[] ch = list.get(i).toCharArray();
            if(ch[j]=='Q'){
                return false;
            }
        }

        return true;
        
    }

    private void placeQueens(int i, int n,List<String> row, List<List<String>> board){

        if(i == n){
            board.add(new ArrayList<>(row));
            return;
        }

        for(int j=0; j<n; j++){
            if(isSafe(i,j,row,n)){
                char[] ch = row.get(i).toCharArray();
                ch[j]='Q';
                row.set(i,new String(ch));
                placeQueens(i+1,n,row,board);
                ch[j]='.';
                row.set(i,new String(ch));
            }
        }

    }
}
```

</details>

---

## Binary Search (8)

### 🟢 704. Binary Search

**Easy** · 🏷️ Array, Binary Search · 📅 2026-03-05

#### 📄 Problem

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

 

Example 1:

```
**Input:** nums = [-1,0,3,5,9,12], target = 9
**Output:** 4
**Explanation:** 9 exists in nums and its index is 4
```

Example 2:

```
**Input:** nums = [-1,0,3,5,9,12], target = 2
**Output:** -1
**Explanation:** 2 does not exist in nums so return -1
```

 

**Constraints:**

	- `1 <= nums.length <= 10^4`
	- `-10^4 < nums[i], target < 10^4`
	- All the integers in `nums` are **unique**.
	- `nums` is sorted in ascending order.

#### 💡 Revision note

```text
Pattern: Binary Search
Key idea: Each comparison eliminates half the remaining elements in a sorted array.
Complexity: O(log n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int search(int[] nums, int target) {

        int n = nums.length;
        
        int l =0 ;
        int h = n-1;

        while(l<=h){
            int m = l +(h-l)/2;
            if(nums[m]==target){
                return m;
            }
            else if(nums[m]>target){
                h=m-1;
            }else{
                l=m+1;
            }
        }
        return -1;
        
    }
}
```

</details>

### 🟡 33. Search in Rotated Sorted Array

**Medium** · 🏷️ Array, Binary Search · 📅 2025-11-08

#### 📄 Problem

There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly left rotated** at an unknown index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be left rotated by `3` indices and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return *the index of *`target`* if it is in *`nums`*, or *`-1`* if it is not in *`nums`.

You must write an algorithm with `O(log n)` runtime complexity.

 

Example 1:

```
**Input:** nums = [4,5,6,7,0,1,2], target = 0
**Output:** 4
```
Example 2:

```
**Input:** nums = [4,5,6,7,0,1,2], target = 3
**Output:** -1
```
Example 3:

```
**Input:** nums = [1], target = 0
**Output:** -1
```

 

**Constraints:**

	- `1 <= nums.length <= 5000`
	- `-10^4 <= nums[i] <= 10^4`
	- All values of `nums` are **unique**.
	- `nums` is an ascending array that is possibly rotated.
	- `-10^4 <= target <= 10^4`

#### 💡 Revision note

```text
Pattern: Two-pass binary search
Key idea: Identify rotation point first; one half is always sorted, enabling efficient binary search.
Complexity: O(log n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int search(int[] nums, int target) {
        int pivot = findPivot(nums,0,nums.length-1);
        if(nums[pivot]==target){
            return pivot;
        }
        if (pivot == 0) {
            return binarySearch(nums, 0, nums.length - 1, target);
        }

        // Decide which side to search
        if (target >= nums[pivot] && target <= nums[nums.length - 1]) {
            return binarySearch(nums, pivot, nums.length - 1, target);
        } else {
            return binarySearch(nums, 0, pivot - 1, target);
        }
    }

    private int binarySearch(int[] arr, int l , int r,int target){
    
        while(l<=r){
            int m = l + (r-l)/2;
            if(arr[m] == target){
                return m;
            }
            if(arr[m]<target){
                l = m+1;
            }else{
                r=m-1;
            }
        }
        return -1;
    }
    private int findPivot(int[] arr, int lo, int hi) {
        while (lo <= hi) {
            if (arr[lo] <= arr[hi])
                return lo;

            int mid = (lo + hi) / 2;

            if (arr[mid] > arr[hi])
                lo = mid + 1;

            else
                hi = mid;
        }

        return lo;
    }
}
```

</details>

### 🟡 74. Search a 2D Matrix

**Medium** · 🏷️ Array, Binary Search, Matrix · 📅 2025-11-07

#### 📄 Problem

You are given an `m x n` integer matrix `matrix` with the following two properties:

	- Each row is sorted in non-decreasing order.
	- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` *if* `target` *is in* `matrix` *or* `false` *otherwise*.

You must write a solution in `O(log(m * n))` time complexity.

 

Example 1:

```
**Input:** matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
**Output:** true
```

Example 2:

```
**Input:** matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
**Output:** false
```

 

**Constraints:**

	- `m == matrix.length`
	- `n == matrix[i].length`
	- `1 <= m, n <= 100`
	- `-10^4 <= matrix[i][j], target <= 10^4`

#### 💡 Revision note

```text
Pattern: Staircase search
Key idea: Starting from a corner, each comparison eliminates either a row or column due to sorted properties.
Complexity: O(m + n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int n = matrix.length;
        int m = matrix[0].length;
        int i = 0;
        int j = m-1;
        

        while(i>=0 && i<n  && j>=0 && j<m){
            System.out.println(matrix[i][j]);
            if(matrix[i][j]==target){
                return true;
            }
            if(matrix[i][j] > target){
                j--;
            }else{
                i++;
            }
        }
        return false;
    }

}
```

</details>

### 🟡 153. Find Minimum in Rotated Sorted Array

**Medium** · 🏷️ Array, Binary Search · 📅 2025-11-07

#### 📄 Problem

Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

	- `[4,5,6,7,0,1,2]` if it was rotated `4` times.
	- `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return *the minimum element of this array*.

You must write an algorithm that runs in `O(log n) time`.

 

Example 1:

```
**Input:** nums = [3,4,5,1,2]
**Output:** 1
**Explanation:** The original array was [1,2,3,4,5] rotated 3 times.
```

Example 2:

```
**Input:** nums = [4,5,6,7,0,1,2]
**Output:** 0
**Explanation:** The original array was [0,1,2,4,5,6,7] and it was rotated 4 times.
```

Example 3:

```
**Input:** nums = [11,13,15,17]
**Output:** 11
**Explanation:** The original array was [11,13,15,17] and it was rotated 4 times.
```

 

**Constraints:**

	- `n == nums.length`
	- `1 <= n <= 5000`
	- `-5000 <= nums[i] <= 5000`
	- All the integers of `nums` are **unique**.
	- `nums` is sorted and rotated between `1` and `n` times.

#### 💡 Revision note

```text
Pattern: Rotation point detection
Key idea: The minimum sits immediately after the only position where an element exceeds its successor.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int findMin(int[] arr) {
        for(int i = 0;i<arr.length-1;i++){
            if(arr[i]>arr[i+1]){
                return arr[i+1];
            }
        }
        return arr[0];
    }
}
```

</details>

### 🟡 167. Two Sum II - Input Array Is Sorted

**Medium** · 🏷️ Array, Two Pointers, Binary Search · 📅 2025-11-03

#### 📄 Problem

Given a **1-indexed** array of integers `numbers` that is already ***sorted in non-decreasing order***, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index_1]` and `numbers[index_2]` where `1 <= index_1 < index_2 <= numbers.length`.

Return* the indices of the two numbers *`index_1`* and *`index_2`*, **each incremented by one,** as an integer array *`[index_1, index_2]`* of length 2.*

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

 

Example 1:

```
**Input:** numbers = [2,7,11,15], target = 9
**Output:** [1,2]
**Explanation:** The sum of 2 and 7 is 9. Therefore, index_1 = 1, index_2 = 2. We return [1, 2].
```

Example 2:

```
**Input:** numbers = [2,3,4], target = 6
**Output:** [1,3]
**Explanation:** The sum of 2 and 4 is 6. Therefore index_1 = 1, index_2 = 3. We return [1, 3].
```

Example 3:

```
**Input:** numbers = [-1,0], target = -1
**Output:** [1,2]
**Explanation:** The sum of -1 and 0 is -1. Therefore index_1 = 1, index_2 = 2. We return [1, 2].
```

 

**Constraints:**

	- `2 <= numbers.length <= 3 * 10^4`
	- `-1000 <= numbers[i] <= 1000`
	- `numbers` is sorted in **non-decreasing order**.
	- `-1000 <= target <= 1000`
	- The tests are generated such that there is **exactly one solution**.

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: Sorted array allows moving pointers inward: increment when undershoot, decrement when overshoot, guaranteeing we find target.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] twoSum(int[] arr, int target) {
        int n = arr.length;
        int l = 0;
        int r = n-1;

        while(l<r){
            if(arr[l]+arr[r] == target){
                return new int[]{l+1,r+1};
            }
            if(arr[l]+arr[r]<target){
                l++;
            }else{
                r--;
            }
        }
        return new int[]{-1};
    }
}
```

</details>

### 🟡 300. Longest Increasing Subsequence

**Medium** · 🏷️ Array, Binary Search, Dynamic Programming · 📅 2026-01-07

#### 📄 Problem

Given an integer array `nums`, return *the length of the longest **strictly increasing ******subsequence***.

 

Example 1:

```
**Input:** nums = [10,9,2,5,3,7,101,18]
**Output:** 4
**Explanation:** The longest increasing subsequence is [2,3,7,101], therefore the length is 4.
```

Example 2:

```
**Input:** nums = [0,1,0,3,2,3]
**Output:** 4
```

Example 3:

```
**Input:** nums = [7,7,7,7,7,7,7]
**Output:** 1
```

 

**Constraints:**

	- `1 <= nums.length <= 2500`
	- `-10^4 <= nums[i] <= 10^4`

 

**Follow up:** Can you come up with an algorithm that runs in `O(n log(n))` time complexity?

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: At each position, decide to include the element (extending any smaller-valued previous subsequence) or exclude it.
Complexity: O(n²) time / O(n²) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int n = nums.length;

        int[][] dp = new int[n+1][n+1];

        for(int i = 0;i<n+1 ; i++){
            Arrays.fill(dp[i],-1);
        }
        return findlong(0,-1,nums,dp,n);
        
    }

    private int findlong(int i, int prev, int[] arr, int[][] dp, int n){

        if(i==n){
            return 0;
        }
        if(dp[i][prev+1]!=-1){
            return dp[i][prev+1];
        }

        int nonpick = findlong(i+1,prev,arr,dp,n);
        int pick = 0;
        if(prev == -1 || arr[i]>arr[prev])  {
            pick = 1 + findlong(i+1,i,arr,dp,n);
        } 
        return dp[i][prev+1]=Integer.max(pick,nonpick);
            
    }
}
```

</details>

### 🟡 875. Koko Eating Bananas

**Medium** · 🏷️ Array, Binary Search · 📅 2025-09-05

#### 📄 Problem

Koko loves to eat bananas. There are `n` piles of bananas, the `i^th` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return *the minimum integer* `k` *such that she can eat all the bananas within* `h` *hours*.

 

Example 1:

```
**Input:** piles = [3,6,7,11], h = 8
**Output:** 4
```

Example 2:

```
**Input:** piles = [30,11,23,4,20], h = 5
**Output:** 30
```

Example 3:

```
**Input:** piles = [30,11,23,4,20], h = 6
**Output:** 23
```

 

**Constraints:**

	- `1 <= piles.length <= 10^4`
	- `piles.length <= h <= 10^9`
	- `1 <= piles[i] <= 10^9`

#### 💡 Revision note

```text
Pattern: Binary search on answer
Key idea: Minimum eating speed satisfies monotonicity; binary search for smallest k where total eating time ≤ h.
Complexity: O(n * log(max(piles))) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minEatingSpeed(int[] arr, int hour) {
        int max = Arrays.stream(arr).max().getAsInt();
        int l = 1;
        int h = max;
        int ans = -1;
        while(l<=h){
            int mid = (l+ h)/2;
            if(checkSpeed(arr,mid,hour)){
                ans = mid;
                h = mid-1;
            }else {
                l = mid+1;
            }
        }
        return ans;
    }
    private boolean checkSpeed(int[] arr, int mid, int hour) {

        long t= 0;
        for (int i = 0; i < arr.length; i++) {
            t += (arr[i]+mid-1)/mid;
        }
        return t<=hour;
    }
}
```

</details>

### 🟡 2554. Maximum Number of Integers to Choose From a Range I

**Medium** · 🏷️ Array, Hash Table, Binary Search, Greedy, Sorting · 📅 2024-12-06

#### 📄 Problem

You are given an integer array `banned` and two integers `n` and `maxSum`. You are choosing some number of integers following the below rules:

	- The chosen integers have to be in the range `[1, n]`.
	- Each integer can be chosen **at most once**.
	- The chosen integers should not be in the array `banned`.
	- The sum of the chosen integers should not exceed `maxSum`.

Return *the **maximum** number of integers you can choose following the mentioned rules*.

 

Example 1:

```
**Input:** banned = [1,6,5], n = 5, maxSum = 6
**Output:** 2
**Explanation:** You can choose the integers 2 and 4.
2 and 4 are from the range [1, 5], both did not appear in banned, and their sum is 6, which did not exceed maxSum.
```

Example 2:

```
**Input:** banned = [1,2,3,4,5,6,7], n = 8, maxSum = 1
**Output:** 0
**Explanation:** You cannot choose any integer while following the mentioned conditions.
```

Example 3:

```
**Input:** banned = [11], n = 7, maxSum = 50
**Output:** 7
**Explanation:** You can choose the integers 1, 2, 3, 4, 5, 6, and 7.
They are from the range [1, 7], all did not appear in banned, and their sum is 28, which did not exceed maxSum.
```

 

**Constraints:**

	- `1 <= banned.length <= 10^4`
	- `1 <= banned[i], n <= 10^4`
	- `1 <= maxSum <= 10^9`

#### 💡 Revision note

```text
Pattern: Greedy smallest-first
Key idea: Picking smallest integers first maximizes count—they consume the least sum budget, allowing more picks.
Complexity: O(n·m) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxCount(int[] banned, int n, int maxSum) {
        int res = 0; 
        long sum = 0;
        for(int i = 1;i <= n ; i++ ){
            boolean exist = findNumberExistInArray(i,banned);
            if(!exist){
                sum+=i;
                if(sum<=maxSum)
                    res+=1;
            }
        }
        return res;
    }

    private boolean findNumberExistInArray(int m,int[] banned){
        for(int j=0 ; j< banned.length ; j++){
            if(banned[j]==m)
                return true;
        }
        return false;
    }
}
```

</details>

---

## Greedy (8)

### 🟡 11. Container With Most Water

**Medium** · 🏷️ Array, Two Pointers, Greedy · 📅 2025-11-04

#### 📄 Problem

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `i^th` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return *the maximum amount of water a container can store*.

**Notice** that you may not slant the container.

 

Example 1:

```
**Input:** height = [1,8,6,2,5,4,8,3,7]
**Output:** 49
**Explanation:** The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```

Example 2:

```
**Input:** height = [1,1]
**Output:** 1
```

 

**Constraints:**

	- `n == height.length`
	- `2 <= n <= 10^5`
	- `0 <= height[i] <= 10^4`

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: Start with maximum width; move the shorter boundary inward since moving the taller one can't increase area.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxArea(int[] arr) {
        int n = arr.length;
        int r = n-1;
        int l = 0;
        int ans = 0;
        while(l<=r){
            if(arr[l]>arr[r]){
                int index = r-l;
                ans = Integer.max(ans, arr[r]*index);
                r--;
            }else{
                int index = r-l;
                ans = Integer.max(ans,arr[l]*index);
                l++;
            }
        }
        return ans;
    }
}
```

</details>

### 🟡 45. Jump Game II

**Medium** · 🏷️ Array, Dynamic Programming, Greedy · 📅 2026-06-13

#### 📄 Problem

You are given a **0-indexed** array of integers `nums` of length `n`. You are initially positioned at index 0.

Each element `nums[i]` represents the maximum length of a forward jump from index `i`. In other words, if you are at index `i`, you can jump to any index `(i + j)` where:

	- `0 <= j <= nums[i]` and
	- `i + j < n`

Return *the minimum number of jumps to reach index *`n - 1`. The test cases are generated such that you can reach index `n - 1`.

 

Example 1:

```
**Input:** nums = [2,3,1,1,4]
**Output:** 2
**Explanation:** The minimum number of jumps to reach the last index is 2. Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

Example 2:

```
**Input:** nums = [2,3,0,1,4]
**Output:** 2
```

 

**Constraints:**

	- `1 <= nums.length <= 10^4`
	- `0 <= nums[i] <= 1000`
	- It's guaranteed that you can reach `nums[n - 1]`.

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: Minimum jumps from position i equals one plus the minimum from all reachable positions.
Complexity: O(n²) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
   
    public int jump(int[] nums) {
        int[] val = new int[nums.length];
        Arrays.fill(val,-1);
        return countJump(0,nums,val);
        
    }

    private int countJump(int i ,  int[] nums, int[] val){

        if(i >=nums.length-1){
            return 0;
        }

       if(val[i]!=-1){
            return val[i];
       }
        int min = 1000000;

       for(int k = 1;k<=nums[i];k++){
            min= Math.min(min,1+countJump(i+k,nums,val));
       }
       return val[i]=min;

    }
}
```

</details>

### 🟡 55. Jump Game

**Medium** · 🏷️ Array, Dynamic Programming, Greedy · 📅 2026-06-13

#### 📄 Problem

You are given an integer array `nums`. You are initially positioned at the array's **first index**, and each element in the array represents your maximum jump length at that position.

Return `true`* if you can reach the last index, or *`false`* otherwise*.

 

Example 1:

```
**Input:** nums = [2,3,1,1,4]
**Output:** true
**Explanation:** Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

Example 2:

```
**Input:** nums = [3,2,1,0,4]
**Output:** false
**Explanation:** You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
```

 

**Constraints:**

	- `1 <= nums.length <= 10^4`
	- `0 <= nums[i] <= 10^5`

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: Memoize reachability from each position and short-circuit upon finding any valid jump path to the end.
Complexity: O(n²) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean canJump(int[] nums) {

        Boolean[] val = new Boolean[nums.length];

        return checkJump(0,nums,val);
        
    }

    private boolean checkJump(int i , int[] nums,Boolean[] val){

        if(i >= nums.length-1){
            return true;
        }

        if (nums[i]==0){
            return false;
        }
        if(val[i]!=null){
            return val[i];
        }

        for(int j = 1;j<=nums[i];j++){
            if(checkJump(i+j,nums,val)){
                return val[i]=true;
            }
        }

        return val[i]=false;
    }
}
```

</details>

### 🟡 122. Best Time to Buy and Sell Stock II

**Medium** · 🏷️ Array, Dynamic Programming, Greedy · 📅 2026-07-11

#### 📄 Problem

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `i^th` day.

On each day, you may decide to buy and/or sell the stock. You can only hold **at most one** share of the stock at any time. However, you can sell and buy the stock multiple times on the **same day**, ensuring you never hold more than one share of the stock.

Find and return *the **maximum** profit you can achieve*.

 

Example 1:

```
**Input:** prices = [7,1,5,3,6,4]
**Output:** 7
**Explanation:** Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
Total profit is 4 + 3 = 7.
```

Example 2:

```
**Input:** prices = [1,2,3,4,5]
**Output:** 4
**Explanation:** Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
Total profit is 4.
```

Example 3:

```
**Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.
```

 

**Constraints:**

	- `1 <= prices.length <= 3 * 10^4`
	- `0 <= prices[i] <= 10^4`

#### 💡 Revision note

```text
Pattern: Greedy peak capture
Key idea: With unlimited free transactions, sum every consecutive daily price increase.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxProfit(int[] arr) {   

        int ans =0;
        for(int i =1 ;i<arr.length;i++) {
            if(arr[i-1]<arr[i]){
                ans = ans + arr[i]-arr[i-1];
            }
        }
        return ans;
    }


    private int findmax(int i, int buy, int[] arr, int[][] dp){
        if( i == arr.length){
            return 0;
        }

        if(dp[i][buy] != -1){
            return dp[i][buy];
        }
        int profit = 0;
        if(buy == 1){
            profit = Integer.max(-arr[i]+findmax(i+1,0,arr,dp) , 0 + findmax(i+1,1,arr,dp));
        }else{
            profit = Integer.max(arr[i]+findmax(i+1,1,arr,dp) , 0 + findmax(i+1,0,arr,dp));
        }
        return dp[i][buy] = profit;
    }

  
}
```

</details>

### 🟡 134. Gas Station

**Medium** · 🏷️ Array, Greedy · 📅 2025-12-04

#### 📄 Problem

There are `n` gas stations along a circular route, where the amount of gas at the `i^th` station is `gas[i]`.

You have a car with an unlimited gas tank and it costs `cost[i]` of gas to travel from the `i^th` station to its next `(i + 1)^th` station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays `gas` and `cost`, return *the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return* `-1`. If there exists a solution, it is **guaranteed** to be **unique**.

 

Example 1:

```
**Input:** gas = [1,2,3,4,5], cost = [3,4,5,1,2]
**Output:** 3
**Explanation:**
Start at station 3 (index 3) and fill up with 4 unit of gas. Your tank = 0 + 4 = 4
Travel to station 4. Your tank = 4 - 1 + 5 = 8
Travel to station 0. Your tank = 8 - 2 + 1 = 7
Travel to station 1. Your tank = 7 - 3 + 2 = 6
Travel to station 2. Your tank = 6 - 4 + 3 = 5
Travel to station 3. The cost is 5. Your gas is just enough to travel back to station 3.
Therefore, return 3 as the starting index.
```

Example 2:

```
**Input:** gas = [2,3,4], cost = [3,4,3]
**Output:** -1
**Explanation:**
You can't start at station 0 or 1, as there is not enough gas to travel to the next station.
Let's start at station 2 and fill up with 4 unit of gas. Your tank = 0 + 4 = 4
Travel to station 0. Your tank = 4 - 3 + 2 = 3
Travel to station 1. Your tank = 3 - 3 + 3 = 3
You cannot travel back to station 2, as it requires 4 unit of gas but you only have 3.
Therefore, you can't travel around the circuit once no matter where you start.
```

 

**Constraints:**

	- `n == gas.length == cost.length`
	- `1 <= n <= 10^5`
	- `0 <= gas[i], cost[i] <= 10^4`
	- The input is generated such that the answer is unique.

#### 💡 Revision note

```text
Pattern: Single-pass greedy
Key idea: If total balance ≥ 0, solution exists. When balance goes negative, all prior starts fail—skip to next candidate.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int total = 0;
        int starting = 0;
        int remain = 0;
        int n = gas.length;

        for(int i=0; i<n; i++){
            total = total + gas[i] - cost[i];
            remain = remain + gas[i] - cost[i];
            if(remain<0){
                remain = 0;
                starting=i+1;
            }
        }
        if(total<0){
            return -1;
        }

        return starting;
        
    }
}
```

</details>

### 🟡 846. Hand of Straights

**Medium** · 🏷️ Array, Hash Table, Greedy, Sorting · 📅 2022-09-09

#### 📄 Problem

Alice has some number of cards and she wants to rearrange the cards into groups so that each group is of size `groupSize`, and consists of `groupSize` consecutive cards.

Given an integer array `hand` where `hand[i]` is the value written on the `i^th` card and an integer `groupSize`, return `true` if she can rearrange the cards, or `false` otherwise.

 

Example 1:

```
**Input:** hand = [1,2,3,6,2,3,4,7,8], groupSize = 3
**Output:** true
**Explanation:** Alice's hand can be rearranged as [1,2,3],[2,3,4],[6,7,8]
```

Example 2:

```
**Input:** hand = [1,2,3,4,5], groupSize = 4
**Output:** false
**Explanation:** Alice's hand can not be rearranged into groups of 4.
```

 

**Constraints:**

	- `1 <= hand.length <= 10^4`
	- `0 <= hand[i] <= 10^9`
	- `1 <= groupSize <= hand.length`

 

**Note:** This question is the same as 1296: https://leetcode.com/problems/divide-array-in-sets-of-k-consecutive-numbers/

#### 💡 Revision note

```text
Pattern: Greedy with sorted counter
Key idea: Process smallest cards first, greedily forming groups; any gap in consecutive requirements means no solution.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Python) — click to expand</b></summary>

```python
class Solution:
    def isNStraightHand(self, hand, groupSize) :
        if len(hand) % groupSize != 0:
            return False
        
        count = collections.Counter(hand)
        keys = sorted(list(count.keys()))
        
        for card in keys:
            if count[card] == 0:
                continue
            total = count[card]
            for n in range(card + 1, card + groupSize):
                count[n] -= total
                if count[n] < 0:
                    return False
            count[card] -= total
        
        return True
```

</details>

### 🟡 2486. Append Characters to String to Make Subsequence

**Medium** · 🏷️ Two Pointers, String, Greedy · 📅 2026-07-12

#### 📄 Problem

You are given two strings `s` and `t` consisting of only lowercase English letters.

Return *the minimum number of characters that need to be appended to the end of *`s`* so that *`t`* becomes a **subsequence** of *`s`.

A **subsequence** is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters.

 

Example 1:

```
**Input:** s = "coaching", t = "coding"
**Output:** 4
**Explanation:** Append the characters "ding" to the end of s so that s = "coachingding".
Now, t is a subsequence of s ("**co**aching**ding**").
It can be shown that appending any 3 characters to the end of s will never make t a subsequence.
```

Example 2:

```
**Input:** s = "abcde", t = "a"
**Output:** 0
**Explanation:** t is already a subsequence of s ("**a**bcde").
```

Example 3:

```
**Input:** s = "z", t = "abcde"
**Output:** 5
**Explanation:** Append the characters "abcde" to the end of s so that s = "zabcde".
Now, t is a subsequence of s ("z**abcde**").
It can be shown that appending any 4 characters to the end of s will never make t a subsequence.
```

 

**Constraints:**

	- `1 <= s.length, t.length <= 10^5`
	- `s` and `t` consist only of lowercase English letters.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int appendCharacters(String s, String t) {
         int n = s.length();
        int m = t.length();
        int i = 0;
        int j = 0;

        while(i<n && j<m){
            if(s.charAt(i) == t.charAt(j)){
                j++;
            }
            i++;
        }
        System.out.println(j);
        return Integer.max(0,t.length()-j);
    }
}
```

</details>

### 🟡 2966. Divide Array Into Arrays With Max Difference

**Medium** · 🏷️ Array, Greedy, Sorting · 📅 2024-02-01

#### 📄 Problem

You are given an integer array `nums` of size `n` where `n` is a multiple of 3 and a positive integer `k`.

Divide the array `nums` into `n / 3` arrays of size **3** satisfying the following condition:

	- The difference between **any** two elements in one array is **less than or equal** to `k`.

Return a **2D** array containing the arrays. If it is impossible to satisfy the conditions, return an empty array. And if there are multiple answers, return **any** of them.

 

Example 1:

**Input:** nums = [1,3,4,8,7,9,3,5,1], k = 2

**Output:** [[1,1,3],[3,4,5],[7,8,9]]

**Explanation:**

The difference between any two elements in each array is less than or equal to 2.

Example 2:

**Input:** nums = [2,4,2,2,5,2], k = 2

**Output:** []

**Explanation:**

Different ways to divide `nums` into 2 arrays of size 3 are:

	- [[2,2,2],[2,4,5]] (and its permutations)
	- [[2,2,4],[2,2,5]] (and its permutations)

Because there are four 2s there will be an array with the elements 2 and 5 no matter how we divide it. since `5 - 2 = 3 > k`, the condition is not satisfied and so there is no valid division.

Example 3:

**Input:** nums = [4,2,9,8,2,12,7,12,10,5,8,5,5,7,9,2,5,11], k = 14

**Output:** [[2,2,2],[4,5,5],[5,5,7],[7,8,8],[9,9,10],[11,12,12]]

**Explanation:**

The difference between any two elements in each array is less than or equal to 14.

 

**Constraints:**

	- `n == nums.length`
	- `1 <= n <= 10^5`
	- `n `is a multiple of 3
	- `1 <= nums[i] <= 10^5`
	- `1 <= k <= 10^5`

#### 💡 Revision note

```text
Pattern: Greedy sorting
Key idea: Consecutive triplets in sorted array minimize max-min; if any triplet exceeds k, no valid division exists.
Complexity: O(n log n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
import java.util.Arrays;
class Solution {
    public int[][] divideArray(int[] nums, int k) {
          int len = nums.length;
        int[][] res = new int[len/3][3];
        Arrays.sort(nums);
        for(int i=0,m=0; i<len; i=i+3,m++){
            res[m][0] = nums[i];
            for(int j=1; j<3; j++){
                if(nums[i+j]-res[m][0]<=k){
                    res[m][j]=nums[i+j];
                } else{
                    return new int[0][0];
                }
            }
        }
        return res;
}}
```

</details>

---

## Matrix (7)

### 🟡 36. Valid Sudoku

**Medium** · 🏷️ Array, Hash Table, Matrix · 📅 2025-11-01

#### 📄 Problem

Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

	- Each row must contain the digits `1-9` without repetition.
	- Each column must contain the digits `1-9` without repetition.
	- Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

**Note:**

	- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
	- Only the filled cells need to be validated according to the mentioned rules.

 

Example 1:

```
**Input:** board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
**Output:** true
```

Example 2:

```
**Input:** board = 
[["8","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
**Output:** false
**Explanation:** Same as Example 1, except with the **5** in the top left corner being modified to **8**. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
```

 

**Constraints:**

	- `board.length == 9`
	- `board[i].length == 9`
	- `board[i][j]` is a digit `1-9` or `'.'`.

#### 💡 Revision note

```text
Pattern: Hash set validation
Key idea: Track which digits appear in each row, column, and box; duplicates invalidate the board.
Complexity: O(1) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        
        int[][] row = new int[10][10];
        int[][] col = new int[10][10];
        int[][] sub = new int[10][10];
        for(int i=0; i<9; i++){
            for(int j = 0; j<9; j++){
                if(board[i][j]=='.'){
                    continue;
                }
                int val = board[i][j]-48;
                if(row[i][val]==1){
                    return false;
                }
                row[i][val]=1;
                if(col[j][val]==1){
                    return false;
                }
                col[j][val]=1;
                int subIn = (i/3)*3 + (j/3);
                if(sub[subIn][val]==1){
                    return false;
                }
                sub[subIn][val]=1;
            }
        }
        return true;
    }
}
```

</details>

### 🟡 63. Unique Paths II

**Medium** · 🏷️ Array, Dynamic Programming, Matrix · 📅 2025-12-29

#### 📄 Problem

You are given an `m x n` integer array `grid`. There is a robot initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

An obstacle and space are marked as `1` or `0` respectively in `grid`. A path that the robot takes cannot include **any** square that is an obstacle.

Return *the number of possible unique paths that the robot can take to reach the bottom-right corner*.

The testcases are generated so that the answer will be less than or equal to `2 * 10^9`.

 

Example 1:

```
**Input:** obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
**Output:** 2
**Explanation:** There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right
```

Example 2:

```
**Input:** obstacleGrid = [[0,1],[0,0]]
**Output:** 1
```

 

**Constraints:**

	- `m == obstacleGrid.length`
	- `n == obstacleGrid[i].length`
	- `1 <= m, n <= 100`
	- `obstacleGrid[i][j]` is `0` or `1`.

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Path count from each cell equals sum of paths from top and left neighbors; memoization prevents redundant recursion.
Complexity: O(m × n) time / O(m × n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int n = obstacleGrid.length;
        int m = obstacleGrid[0].length;
    

        int[][] dp = new int[n][m];
        for(int i =0 ;i<n; i++){
            Arrays.fill(dp[i],-1);
        }
        
        return findpath(n-1,m-1,obstacleGrid,dp);
    }

    private int findpath(int i,int j , int[][] arr,int[][] dp){

        if(i==0 && j==0){
            return arr[i][j] == 0 ? 1:0;
        }
        if(i<0 || j<0 || arr[i][j]==1){
            return 0;
        }

        if(dp[i][j]!=-1){
            return dp[i][j];
        }
        int up = findpath(i-1,j,arr,dp);
        int le = findpath(i,j-1,arr,dp);

        return dp[i][j]=up+le;
    }
}
```

</details>

### 🟡 64. Minimum Path Sum

**Medium** · 🏷️ Array, Dynamic Programming, Matrix · 📅 2025-12-29

#### 📄 Problem

Given a `m x n` `grid` filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

 

Example 1:

```
**Input:** grid = [[1,3,1],[1,5,1],[4,2,1]]
**Output:** 7
**Explanation:** Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.
```

Example 2:

```
**Input:** grid = [[1,2,3],[4,5,6]]
**Output:** 12
```

 

**Constraints:**

	- `m == grid.length`
	- `n == grid[i].length`
	- `1 <= m, n <= 200`
	- `0 <= grid[i][j] <= 200`

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Minimum path = cell value + minimum of paths from above/left; memoization avoids redundant subproblem calculations.
Complexity: O(m*n) time / O(m*n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minPathSum(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;
        int[][] dp = new int[n][m];

        for(int i = 0;i<n; i++){
            Arrays.fill(dp[i],-1);
        }
        return findmin(n-1,m-1,grid,dp);
        
    }


    private int findmin(int i, int j, int[][] arr, int[][] dp){

        if(i == 0 && j == 0){
            return arr[i][j];
        }

        if(i<0 || j<0){
            return (int) 1e9 ;
        }

        if(dp[i][j] != -1){
            return dp[i][j];
        }

        int up = arr[i][j] + findmin(i-1,j,arr,dp);
        int le = arr[i][j] + findmin(i,j-1,arr,dp);
        System.out.println(up);
        System.out.println(le);

        return dp[i][j] = Integer.min(up,le);
    }
}
```

</details>

### 🟡 417. Pacific Atlantic Water Flow

**Medium** · 🏷️ Array, Depth-First Search, Breadth-First Search, Matrix · 📅 2026-04-02

#### 📄 Problem

There is an `m x n` rectangular island that borders both the **Pacific Ocean** and **Atlantic Ocean**. The **Pacific Ocean** touches the island's left and top edges, and the **Atlantic Ocean** touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an `m x n` integer matrix `heights` where `heights[r][c]` represents the **height above sea level** of the cell at coordinate `(r, c)`.

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is **less than or equal to** the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return *a **2D list** of grid coordinates *`result`* where *`result[i] = [r_i, c_i]`* denotes that rain water can flow from cell *`(r_i, c_i)`* to **both** the Pacific and Atlantic oceans*.

 

Example 1:

```
**Input:** heights = [[1,2,2,3,5],[3,2,3,4,4],[2,4,5,3,1],[6,7,1,4,5],[5,1,1,2,4]]
**Output:** [[0,4],[1,3],[1,4],[2,2],[3,0],[3,1],[4,0]]
**Explanation:** The following cells can flow to the Pacific and Atlantic oceans, as shown below:
[0,4]: [0,4] -> Pacific Ocean 
       [0,4] -> Atlantic Ocean
[1,3]: [1,3] -> [0,3] -> Pacific Ocean 
       [1,3] -> [1,4] -> Atlantic Ocean
[1,4]: [1,4] -> [1,3] -> [0,3] -> Pacific Ocean 
       [1,4] -> Atlantic Ocean
[2,2]: [2,2] -> [1,2] -> [0,2] -> Pacific Ocean 
       [2,2] -> [2,3] -> [2,4] -> Atlantic Ocean
[3,0]: [3,0] -> Pacific Ocean 
       [3,0] -> [4,0] -> Atlantic Ocean
[3,1]: [3,1] -> [3,0] -> Pacific Ocean 
       [3,1] -> [4,1] -> Atlantic Ocean
[4,0]: [4,0] -> Pacific Ocean 
       [4,0] -> Atlantic Ocean
Note that there are other possible paths for these cells to flow to the Pacific and Atlantic oceans.
```

Example 2:

```
**Input:** heights = [[1]]
**Output:** [[0,0]]
**Explanation:** The water can flow from the only cell to the Pacific and Atlantic oceans.
```

 

**Constraints:**

	- `m == heights.length`
	- `n == heights[r].length`
	- `1 <= m, n <= 200`
	- `0 <= heights[r][c] <= 10^5`

#### 💡 Revision note

```text
Pattern: Boundary-based reverse DFS
Key idea: Search backward from ocean edges (uphill) to find cells reachable from both oceans.
Complexity: O(m*n) time / O(m*n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

    int[] rr = {0,0,-1,1};
    int[] cc = {1,-1,0,0};
    public List<List<Integer>> pacificAtlantic(int[][] arr) {

        int n = arr.length;
        int m = arr[0].length;

        List<List<Integer>> list = new ArrayList<>();

        int[][] vis1 = new int[n][m];
        for(int j=0; j<m; j++){
            dfs(0,j,vis1,arr,n,m);
        }
        for(int i = 0; i<n; i++){
            dfs(i,0,vis1,arr,n,m);
        }
        int[][] vis2 = new int[n][m];
        for(int i=0; i<n; i++){
            dfs(i,m-1,vis2,arr,n,m);
        }
        for(int j = m-1; j>=0; j--){
            dfs(n-1,j,vis2,arr,n,m);
        }

        for(int i = 0;i<n;i++){
            for(int j = 0;j<m;j++){
                if(vis1[i][j]==1 && vis2[i][j]==1){
                    list.add(List.of(i,j));
                }
            }
        }

        return list;


    }

    private void dfs(int i , int j, int[][] vis, int[][] arr,int n, int m){


        if(i<0 || j<0 || i>=n || j>=m || vis[i][j]==1){
            return ;
        }
        vis[i][j]=1;

        for(int k = 0; k< 4 ;k++){
            int idx = rr[k]+i;
            int idy = cc[k]+j;
            if(idx<0 || idy<0 || idx>=n || idy>=m ){
                continue;
            }
            if(arr[idx][idy]>=arr[i][j]){
                dfs(idx,idy,vis,arr,n,m);
            }
            
        }
    

    }
}
```

</details>

### 🟡 931. Minimum Falling Path Sum

**Medium** · 🏷️ Array, Dynamic Programming, Matrix · 📅 2025-12-30

#### 📄 Problem

Given an `n x n` array of integers `matrix`, return *the **minimum sum** of any **falling path** through* `matrix`.

A **falling path** starts at any element in the first row and chooses the element in the next row that is either directly below or diagonally left/right. Specifically, the next element from position `(row, col)` will be `(row + 1, col - 1)`, `(row + 1, col)`, or `(row + 1, col + 1)`.

 

Example 1:

```
**Input:** matrix = [[2,1,3],[6,5,4],[7,8,9]]
**Output:** 13
**Explanation:** There are two falling paths with a minimum sum as shown.
```

Example 2:

```
**Input:** matrix = [[-19,57],[-40,-5]]
**Output:** -59
**Explanation:** The falling path with a minimum sum is shown.
```

 

**Constraints:**

	- `n == matrix.length == matrix[i].length`
	- `1 <= n <= 100`
	- `-100 <= matrix[i][j] <= 100`

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Each cell's minimum path depends only on the minimum of three cells above; memoization prevents recomputing overlapping subproblems.
Complexity: O(n²) time / O(n²) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minFallingPathSum(int[][] matrix) {
        int n = matrix.length;


        int min = (int) 1e9;

        int[][] dp = new int[n][n];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],(int)1e9);
        }

        for(int i = 0;i<n;i++){
            min = Integer.min(min,minfallingpath(n-1,i,n,matrix,dp));

        }
        return min;
        
        
    }

    private int minfallingpath(int i, int j ,int n, int[][] matrix, int[][] dp){

        if(i == 0 && j>=0 && j<n){
            return matrix[i][j];
        }

        if(i<0 || j<0 || i==n || j ==n){
            return (int) 1e9;
        }

        if(dp[i][j]!=(int)1e9){
            return dp[i][j];
        }

        int up = matrix[i][j] + minfallingpath(i-1,j,n,matrix,dp);
        int left = matrix[i][j] + minfallingpath(i-1,j-1,n,matrix,dp);
        int right = matrix[i][j] + minfallingpath(i-1,j+1,n,matrix,dp);

        return dp[i][j]=Integer.min(Integer.min(up,left),right);
    }
}
```

</details>

### 🟡 994. Rotting Oranges

**Medium** · 🏷️ Array, Breadth-First Search, Matrix · 📅 2026-04-01

#### 📄 Problem

You are given an `m x n` `grid` where each cell can have one of three values:

	- `0` representing an empty cell,
	- `1` representing a fresh orange, or
	- `2` representing a rotten orange.

Every minute, any fresh orange that is **4-directionally adjacent** to a rotten orange becomes rotten.

Return *the minimum number of minutes that must elapse until no cell has a fresh orange*. If *this is impossible, return* `-1`.

 

Example 1:

```
**Input:** grid = [[2,1,1],[1,1,0],[0,1,1]]
**Output:** 4
```

Example 2:

```
**Input:** grid = [[2,1,1],[0,1,1],[1,0,1]]
**Output:** -1
**Explanation:** The orange in the bottom left corner (row 2, column 0) is never rotten, because rotting only happens 4-directionally.
```

Example 3:

```
**Input:** grid = [[0,2]]
**Output:** 0
**Explanation:** Since there are already no fresh oranges at minute 0, the answer is just 0.
```

 

**Constraints:**

	- `m == grid.length`
	- `n == grid[i].length`
	- `1 <= m, n <= 10`
	- `grid[i][j]` is `0`, `1`, or `2`.

#### 💡 Revision note

```text
Pattern: Multi-source BFS
Key idea: Start from all rotten oranges simultaneously; each BFS level represents one minute, naturally giving the minimum time needed.
Complexity: O(m × n) time / O(m × n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

    int[] rr = {0,0,-1,1};
    int[] cc = {-1,1,0,0};
    public int orangesRotting(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;

        int[][] vis = new int[n][m];
        Queue<List<Integer>> queue = new LinkedList<>();

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++ ){
                if(grid[i][j] == 2){
                    queue.offer(List.of(i,j));
                }
            }
        }

        int ans = bfs(queue,grid,n,m);
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++ ){
                if(grid[i][j] == 1){
                    return -1;
                }
            }
        }
        return ans;
    }


    private int bfs(Queue<List<Integer>> queue,int[][] grid, int n , int m){
        int ans = 0;

        while(!queue.isEmpty()){
            int size = queue.size();
                boolean flag = false;

            for (int s = 0; s < size; s++){
                List<Integer> list = queue.poll();
                int i = list.get(0);
                int j = list.get(1);

                for(int k=0; k<4; k++){
                    int idx = rr[k] + i;
                    int idy = cc[k] + j;

                    if(idx >=0 && idx<n && idy >=0 && idy<m && grid[idx][idy] == 1){
                        flag = true;
                        grid[idx][idy] = 2;
                        queue.offer(List.of(idx,idy));
                    }
                }
            }
            if(flag)
            ans++;
            
        }

        return ans;
    }
}
```

</details>

### 🔴 1289. Minimum Falling Path Sum II

**Hard** · 🏷️ Array, Dynamic Programming, Matrix · 📅 2025-12-30

#### 📄 Problem

Given an `n x n` integer matrix `grid`, return *the minimum sum of a **falling path with non-zero shifts***.

A **falling path with non-zero shifts** is a choice of exactly one element from each row of `grid` such that no two elements chosen in adjacent rows are in the same column.

 

Example 1:

```
**Input:** grid = [[1,2,3],[4,5,6],[7,8,9]]
**Output:** 13
**Explanation:** 
The possible falling paths are:
[1,5,9], [1,5,7], [1,6,7], [1,6,8],
[2,4,8], [2,4,9], [2,6,7], [2,6,8],
[3,4,8], [3,4,9], [3,5,7], [3,5,9]
The falling path with the smallest sum is [1,5,7], so the answer is 13.
```

Example 2:

```
**Input:** grid = [[7]]
**Output:** 7
```

 

**Constraints:**

	- `n == grid.length == grid[i].length`
	- `1 <= n <= 200`
	- `-99 <= grid[i][j] <= 99`

#### 💡 Revision note

```text
Pattern: Top-down DP with memoization
Key idea: Each cell's optimal value depends on all other columns in the previous row; memoization caches these values.
Complexity: O(n³) time / O(n²) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int minFallingPathSum(int[][] grid) {

        int n = grid.length;
        int ans = (int)1e9;

        int[][] dp = new int[n][n];
        for(int i =0;i<n;i++){
            Arrays.fill(dp[i],(int)1e9);
        }
        for(int i = 0;i<n;i++){
            ans = Integer.min(ans,findmin(n-1,i,grid,n,dp));
        }

        return ans;
        
    }

    private int findmin(int i, int last, int[][] grid, int n,int[][] dp){

        if(i ==0 && last>=0 && last<n){
            return grid[i][last];
        }

        if(i<0 || last<0 || i==n || last==n){
            return (int)1e9;
        }

        if(dp[i][last]!=(int)1e9){
            return dp[i][last];
        }

        int min = (int)1e9;

        for(int next = 0; next<n; next++){
            if(next!=last){
                min = Integer.min(min, grid[i][last] + findmin(i-1,next,grid,n,dp));

            }
        }
        return dp[i][last]=min;
    }
}
```

</details>

---

## Database (5)

### 🟢 511. Game Play Analysis I

**Easy** · 🏷️ Database · 📅 2024-12-17

#### 📄 Problem

Table: `Activity`

```
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| player_id    | int     |
| device_id    | int     |
| event_date   | date    |
| games_played | int     |
+--------------+---------+
(player_id, event_date) is the primary key (combination of columns with unique values) of this table.
This table shows the activity of players of some games.
Each row is a record of a player who logged in and played a number of games (possibly 0) before logging out on someday using some device.
```

 

Write a solution to find the **first login date** for each player.

Return the result table in **any order**.

The result format is in the following example.

 

Example 1:

```
**Input:** 
Activity table:
+-----------+-----------+------------+--------------+
| player_id | device_id | event_date | games_played |
+-----------+-----------+------------+--------------+
| 1         | 2         | 2016-03-01 | 5            |
| 1         | 2         | 2016-05-02 | 6            |
| 2         | 3         | 2017-06-25 | 1            |
| 3         | 1         | 2016-03-02 | 0            |
| 3         | 4         | 2018-07-03 | 5            |
+-----------+-----------+------------+--------------+
**Output:** 
+-----------+-------------+
| player_id | first_login |
+-----------+-------------+
| 1         | 2016-03-01  |
| 2         | 2017-06-25  |
| 3         | 2016-03-02  |
+-----------+-------------+
```

#### 💡 Revision note

```text
Pattern: GROUP BY aggregation
Key idea: Grouping by player_id and taking the minimum date directly identifies each player's first login.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (MySQL) — click to expand</b></summary>

```sql
# Write your MySQL query statement below
select player_id, min(date(event_date)) as first_login from Activity group by player_id
```

</details>

### 🟢 595. Big Countries

**Easy** · 🏷️ Database · 📅 2022-09-05

#### 📄 Problem

Table: `World`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |
+-------------+---------+
name is the primary key (column with unique values) for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.
```

 

A country is **big** if:

	- it has an area of at least three million (i.e., `3000000 km^2`), or
	- it has a population of at least twenty-five million (i.e., `25000000`).

Write a solution to find the name, population, and area of the **big countries**.

Return the result table in **any order**.

The result format is in the following example.

 

Example 1:

```
**Input:** 
World table:
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
**Output:** 
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+
```

#### 💡 Revision note

```text
Pattern: OR filtering
Key idea: Problem definition uses OR logic, so WHERE clause with OR directly encodes the big country criteria.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (MySQL) — click to expand</b></summary>

```sql
# Write your MySQL query statement below
select name,population,area from world where area>=3000000 or population>=25000000;
```

</details>

### 🟢 596. Classes With at Least 5 Students

**Easy** · 🏷️ Database · 📅 2022-09-05

#### 📄 Problem

Table: `Courses`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| student     | varchar |
| class       | varchar |
+-------------+---------+
(student, class) is the primary key (combination of columns with unique values) for this table.
Each row of this table indicates the name of a student and the class in which they are enrolled.
```

 

Write a solution to find all the classes that have **at least five students**.

Return the result table in **any order**.

The result format is in the following example.

 

Example 1:

```
**Input:** 
Courses table:
+---------+----------+
| student | class    |
+---------+----------+
| A       | Math     |
| B       | English  |
| C       | Math     |
| D       | Biology  |
| E       | Math     |
| F       | Computer |
| G       | Math     |
| H       | Math     |
| I       | Math     |
+---------+----------+
**Output:** 
+---------+
| class   |
+---------+
| Math    |
+---------+
**Explanation:** 
- Math has 6 students, so we include it.
- English has 1 student, so we do not include it.
- Biology has 1 student, so we do not include it.
- Computer has 1 student, so we do not include it.
```

#### 💡 Revision note

```text
Pattern: GROUP BY with HAVING
Key idea: Group rows by class with GROUP BY, then filter using HAVING for count >= 5.
Complexity: O(n) time / O(k) space
```

<details><summary><b>🧩 Solution (MySQL) — click to expand</b></summary>

```sql
# Write your MySQL query statement below
select class from courses group by class having count(class)>=5;
```

</details>

### 🟢 1084. Sales Analysis III

**Easy** · 🏷️ Database · 📅 2024-12-17

#### 📄 Problem

Table: `Product`

```
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| product_id   | int     |
| product_name | varchar |
| unit_price   | int     |
+--------------+---------+
product_id is the primary key (column with unique values) of this table.
Each row of this table indicates the name and the price of each product.
```

Table: `Sales`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| seller_id   | int     |
| product_id  | int     |
| buyer_id    | int     |
| sale_date   | date    |
| quantity    | int     |
| price       | int     |
+-------------+---------+
This table can have duplicate rows.
product_id is a foreign key (reference column) to the Product table.
Each row of this table contains some information about one sale.
```

 

Write a solution to report the **products** that were **only** sold in the first quarter of `2019`. That is, between `2019-01-01` and `2019-03-31` inclusive.

Return the result table in **any order**.

The result format is in the following example.

 

Example 1:

```
**Input:** 
Product table:
+------------+--------------+------------+
| product_id | product_name | unit_price |
+------------+--------------+------------+
| 1          | S8           | 1000       |
| 2          | G4           | 800        |
| 3          | iPhone       | 1400       |
+------------+--------------+------------+
Sales table:
+-----------+------------+----------+------------+----------+-------+
| seller_id | product_id | buyer_id | sale_date  | quantity | price |
+-----------+------------+----------+------------+----------+-------+
| 1         | 1          | 1        | 2019-01-21 | 2        | 2000  |
| 1         | 2          | 2        | 2019-02-17 | 1        | 800   |
| 2         | 2          | 3        | 2019-06-02 | 1        | 800   |
| 3         | 3          | 4        | 2019-05-13 | 2        | 2800  |
+-----------+------------+----------+------------+----------+-------+
**Output:** 
+-------------+--------------+
| product_id  | product_name |
+-------------+--------------+
| 1           | S8           |
+-------------+--------------+
**Explanation:** 
The product with id 1 was only sold in the spring of 2019.
The product with id 2 was sold in the spring of 2019 but was also sold after the spring of 2019.
The product with id 3 was sold after spring 2019.
We return only product 1 as it is the product that was only sold in the spring of 2019.
```

#### 💡 Revision note

```text
Pattern: MIN/MAX boundary filtering
Key idea: Check only the first and last sale per product—if both are in Q1, all others must be too.
Complexity: O(n) time / O(m) space
```

<details><summary><b>🧩 Solution (PostgreSQL) — click to expand</b></summary>

```sql
SELECT p.product_id, p.product_name
FROM product p JOIN sales s USING(product_id)
GROUP BY p.product_id, p.product_name
HAVING MIN(s.sale_date) >= '2019-01-01' AND MAX(s.sale_date) <= '2019-03-31';
```

</details>

### 🟢 1757. Recyclable and Low Fat Products

**Easy** · 🏷️ Database · 📅 2022-09-09

#### 📄 Problem

Table: `Products`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
product_id is the primary key (column with unique values) for this table.
low_fats is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.
```

 

Write a solution to find the ids of products that are both low fat and recyclable.

Return the result table in **any order**.

The result format is in the following example.

 

Example 1:

```
**Input:** 
Products table:
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
**Output:** 
+-------------+
| product_id  |
+-------------+
| 1           |
| 3           |
+-------------+
**Explanation:** Only products 1 and 3 are both low fat and recyclable.
```

#### 💡 Revision note

```text
Pattern: Conditional filtering
Key idea: AND operator in WHERE clause filters rows matching all specified conditions.
Complexity: O(n) time / O(k) space
```

<details><summary><b>🧩 Solution (MySQL) — click to expand</b></summary>

```sql
# Write your MySQL query statement below
SELECT PRODUCT_ID FROM PRODUCTS WHERE LOW_FATS='Y' AND RECYCLABLE='Y';
```

</details>

---

## Monotonic Stack (5)

### 🟡 503. Next Greater Element II

**Medium** · 🏷️ Array, Stack, Monotonic Stack · 📅 2026-05-10

#### 📄 Problem

Given a circular integer array `nums` (i.e., the next element of `nums[nums.length - 1]` is `nums[0]`), return *the **next greater number** for every element in* `nums`.

The **next greater number** of a number `x` is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return `-1` for this number.

 

Example 1:

```
**Input:** nums = [1,2,1]
**Output:** [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number. 
The second 1's next greater number needs to search circularly, which is also 2.
```

Example 2:

```
**Input:** nums = [1,2,3,4,3]
**Output:** [2,3,4,-1,4]
```

 

**Constraints:**

	- `1 <= nums.length <= 10^4`
	- `-10^9 <= nums[i] <= 10^9`

#### 💡 Revision note

```text
Pattern: Monotonic decreasing stack
Key idea: Decreasing stack ensures next greater element is always at top; two passes handle circularity.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {

        int n = nums.length;

        Stack<Integer> s = new Stack<>();

        int[] res = new int[n];

        for(int i = n-1; i>=0;i--){

            while(!s.isEmpty() && nums[i]>=s.peek()){
                s.pop();
            }

            if(s.isEmpty()){
                res[i] = nextGFromF(nums,nums[i]);
                
            }else{
                res[i]=s.peek();
            }
            s.push(nums[i]);
        }

        return res;
        
    }

    private int nextGFromF(int[] nums, int k){

        for(int i =0; i<nums.length ;i++){
            if(nums[i]>k){
                return nums[i];
            }
        }
        return -1;
    }
}
```

</details>

### 🟡 739. Daily Temperatures

**Medium** · 🏷️ Array, Stack, Monotonic Stack · 📅 2025-11-05

#### 📄 Problem

Given an array of integers `temperatures` represents the daily temperatures, return *an array* `answer` *such that* `answer[i]` *is the number of days you have to wait after the* `i^th` *day to get a warmer temperature*. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

 

Example 1:

```
**Input:** temperatures = [73,74,75,71,69,72,76,73]
**Output:** [1,1,4,2,1,1,0,0]
```
Example 2:

```
**Input:** temperatures = [30,40,50,60]
**Output:** [1,1,1,0]
```
Example 3:

```
**Input:** temperatures = [30,60,90]
**Output:** [1,1,0]
```

 

**Constraints:**

	- `1 <= temperatures.length <= 10^5`
	- `30 <= temperatures[i] <= 100`

#### 💡 Revision note

```text
Pattern: Monotonic stack
Key idea: Monotonic decreasing stack guarantees nearest warmer temperature is found without revisiting previous days.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] dailyTemperatures(int[] temp) {
        Stack<Integer> stack = new Stack<>();

        int n = temp.length;
        int[] ans = new int[n];
        ans[n-1]=0;
        stack.push(n-1);
        for(int i=n-2; i>=0; i--){
            while(!stack.isEmpty() && temp[stack.peek()]<=temp[i]){
                stack.pop();
            }
            if(!stack.isEmpty()){
                ans[i]=stack.peek()-i;
            }else{
                ans[i]=0;
            }
            stack.push(i);
        }

        Collections.reverse(Arrays.asList(ans));
        return ans;
    }
}
```

</details>

### 🟡 853. Car Fleet

**Medium** · 🏷️ Array, Stack, Sorting, Monotonic Stack · 📅 2025-11-07

#### 📄 Problem

There are `n` cars at given miles away from the starting mile 0, traveling to reach the mile `target`.

You are given two integer arrays `position` and `speed`, both of length `n`, where `position[i]` is the starting mile of the `i^th` car and `speed[i]` is the speed of the `i^th` car in miles per hour.

A car cannot pass another car, but it can catch up and then travel next to it at the speed of the slower car.

A **car fleet** is a single car or a group of cars driving next to each other. The speed of the car fleet is the **minimum** speed of any car in the fleet.

If a car catches up to a car fleet at the mile `target`, it will still be considered as part of the car fleet.

Return the number of car fleets that will arrive at the destination.

 

Example 1:

**Input:** target = 12, position = [10,8,0,5,3], speed = [2,4,1,1,3]

**Output:** 3

**Explanation:**

	- The cars starting at 10 (speed 2) and 8 (speed 4) become a fleet, meeting each other at 12. The fleet forms at `target`.
	- The car starting at 0 (speed 1) does not catch up to any other car, so it is a fleet by itself.
	- The cars starting at 5 (speed 1) and 3 (speed 3) become a fleet, meeting each other at 6. The fleet moves at speed 1 until it reaches `target`.

Example 2:

**Input:** target = 10, position = [3], speed = [3]

**Output:** 1

**Explanation:**

There is only one car, hence there is only one fleet.

Example 3:

**Input:** target = 100, position = [0,2,4], speed = [4,2,1]

**Output:** 1

**Explanation:**

	- The cars starting at 0 (speed 4) and 2 (speed 2) become a fleet, meeting each other at 4. The car starting at 4 (speed 1) travels to 5.
	- Then, the fleet at 4 (speed 2) and the car at position 5 (speed 1) become one fleet, meeting each other at 6. The fleet moves at speed 1 until it reaches `target`.

 

**Constraints:**

	- `n == position.length == speed.length`
	- `1 <= n <= 10^5`
	- `0 < target <= 10^6`
	- `0 <= position[i] < target`
	- All the values of `position` are **unique**.
	- `0 < speed[i] <= 10^6`

#### 💡 Revision note

```text
Pattern: Sort by Position + Greedy
Key idea: Right-to-left greedy: new fleet only if arrival time exceeds previous; otherwise catches up and merges.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int carFleet(int target, int[] position, int[] speed) {
        int n = position.length;
        Integer[] indices = new Integer[n];
        for(int i = 0;i<n;i++){
            indices[i]=i;
        }
        Arrays.sort(indices,(i, j) -> Integer.compare(position[j], position[i]));
        int ans = 0;
        double preArrivalTime = 0;
        for(int ind :  indices){
            double arrivalTime = (double)(target - position[ind])/speed[ind];
            if(arrivalTime > preArrivalTime){
                ans++;
                preArrivalTime = arrivalTime;
            }
        }
        return ans;

        


    }
}
```

</details>

### 🔴 42. Trapping Rain Water

**Hard** · 🏷️ Array, Two Pointers, Dynamic Programming, Stack, Monotonic Stack · 📅 2025-11-04

#### 📄 Problem

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

 

Example 1:

```
**Input:** height = [0,1,0,2,1,0,1,3,2,1,2,1]
**Output:** 6
**Explanation:** The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.
```

Example 2:

```
**Input:** height = [4,2,0,3,2,5]
**Output:** 9
```

 

**Constraints:**

	- `n == height.length`
	- `1 <= n <= 2 * 10^4`
	- `0 <= height[i] <= 10^5`

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: Process from the side with smaller max height; water level equals min of left/right maximums.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int trap(int[] arr) {

        int n = arr.length;
        int lmax = arr[0];
        int rmax = arr[n-1];
        int l = 1;
        int r = n-2;
        int ans = 0;
        while(l<=r){
            if(lmax>=rmax){
               ans+=Integer.max(0,rmax-arr[r]);
               rmax=Integer.max(rmax,arr[r]);
                r--;
            }else{
                ans+=Integer.max(0,lmax-arr[l]);
                lmax=Integer.max(lmax,arr[l]);
                l++;
            }
        }
        return ans;
        
    }
}
```

</details>

### 🔴 84. Largest Rectangle in Histogram

**Hard** · 🏷️ Array, Stack, Monotonic Stack · 📅 2025-10-30

#### 📄 Problem

Given an array of integers `heights` representing the histogram's bar height where the width of each bar is `1`, return *the area of the largest rectangle in the histogram*.

 

Example 1:

```
**Input:** heights = [2,1,5,6,2,3]
**Output:** 10
**Explanation:** The above is a histogram where width of each bar is 1.
The largest rectangle is shown in the red area, which has an area = 10 units.
```

Example 2:

```
**Input:** heights = [2,4]
**Output:** 4
```

 

**Constraints:**

	- `1 <= heights.length <= 10^5`
	- `0 <= heights[i] <= 10^4`

#### 💡 Revision note

```text
Pattern: Monotonic Stack (Next/Previous Smaller)
Key idea: For each bar, find how far left and right it extends by locating nearest smaller elements on both sides; area equals height times that span.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int largestRectangleArea(int[] heights) {
        if(heights.length==1){
            return heights[0];
        }
        // if(heights.length ==2 ){
        //     return Integer.max(heights[0],heights[1]);
        // }
        int[] nse = nextSmallerElement(heights);
        int[] pse = previousSmallerElement(heights);

        // for(int i = 0;i<heights.length;i++){
        //     System.out.print(nse[i] + " "+ pse[i]);
        //     System.out.println();
        // }
        int ans =0;
        for(int i =0;i<heights.length; i++){
            int width = nse[i]-pse[i]-1;
            ans = Integer.max(ans,width*heights[i]);
        }
        
        return ans;
    }

    private int[] nextSmallerElement(int[] arr){
        int n = arr.length;
        Stack<Integer> q = new Stack<>();
        int[] ans = new int[arr.length];
        ans[n-1] = n;
        q.push(n-1);
        for(int i = n-2; i>=0; i-- ){
            while(!q.isEmpty() && arr[q.peek()]>=arr[i]){
                q.pop();
            }
            if(q.isEmpty()){
                ans[i]=n;
            }else{
                ans[i]=q.peek();
            }
            q.push(i);
        }

        Collections.reverse(Arrays.asList(ans));
        return ans;
    }

    private int[] previousSmallerElement(int[] arr){
        int n = arr.length;
        Stack<Integer> q = new Stack<>();
        int[] ans = new int[arr.length];
        ans[0] = -1;
        q.push(0);
        for(int i = 1; i<n; i++ ){
            while(!q.isEmpty() && arr[q.peek()]>arr[i]){
                q.pop();
            }
            if(q.isEmpty()){
                ans[i] = -1;
            }else{
                ans[i]=q.peek();
            }
            q.push(i);
        }

        return ans;
    }
}
```

</details>

---

## Recursion (5)

### 🟢 21. Merge Two Sorted Lists

**Easy** · 🏷️ Linked List, Recursion · 📅 2025-11-14

#### 📄 Problem

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return *the head of the merged linked list*.

 

Example 1:

```
**Input:** list1 = [1,2,4], list2 = [1,3,4]
**Output:** [1,1,2,3,4,4]
```

Example 2:

```
**Input:** list1 = [], list2 = []
**Output:** []
```

Example 3:

```
**Input:** list1 = [], list2 = [0]
**Output:** [0]
```

 

**Constraints:**

	- The number of nodes in both lists is in the range `[0, 50]`.
	- `-100 <= Node.val <= 100`
	- Both `list1` and `list2` are sorted in **non-decreasing** order.

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: Compare front elements of both sorted lists and always append the smaller one to maintain sorted order.
Complexity: O(m + n) time / O(m + n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode res = new ListNode();
        ListNode curr = res;
        while(list1 != null && list2 != null){
            if(list1.val <= list2.val){
                curr.next = new ListNode(list1.val);
                list1 = list1.next;
            }
            else{
                curr.next = new ListNode(list2.val);
                list2 = list2.next;
            }
            curr = curr.next;
        }

        while(list1 != null){
            curr.next = new ListNode(list1.val);
            list1 = list1.next;
            curr = curr.next;
        }
        while(list2 != null){
            curr.next = new ListNode(list2.val);
            list2 = list2.next;
            curr = curr.next;
        }

        return res.next;
    }

    private ListNode reverse(ListNode head){

        ListNode prev = null;
        ListNode curr = head;
        ListNode temp;

        while(curr != null){
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr =temp;
        }
        return prev;
    }
}
```

</details>

### 🟢 206. Reverse Linked List

**Easy** · 🏷️ Linked List, Recursion · 📅 2025-11-14

#### 📄 Problem

Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

 

Example 1:

```
**Input:** head = [1,2,3,4,5]
**Output:** [5,4,3,2,1]
```

Example 2:

```
**Input:** head = [1,2]
**Output:** [2,1]
```

Example 3:

```
**Input:** head = []
**Output:** []
```

 

**Constraints:**

	- The number of nodes in the list is the range `[0, 5000]`.
	- `-5000 <= Node.val <= 5000`

 

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

#### 💡 Revision note

```text
Pattern: Iterative pointer reversal
Key idea: Reverse each link by saving the next node first, then redirecting current to point to previous.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        
        ListNode curr = head;

        ListNode prev = null;
        ListNode temp;

        while(curr!=null){
            temp = curr.next;
            curr.next = prev;
            prev=curr;
            curr=temp;
            
        }

        return prev;

    }
}
```

</details>

### 🟡 2. Add Two Numbers

**Medium** · 🏷️ Linked List, Math, Recursion · 📅 2025-11-15

#### 📄 Problem

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

 

Example 1:

```
**Input:** l1 = [2,4,3], l2 = [5,6,4]
**Output:** [7,0,8]
**Explanation:** 342 + 465 = 807.
```

Example 2:

```
**Input:** l1 = [0], l2 = [0]
**Output:** [0]
```

Example 3:

```
**Input:** l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
**Output:** [8,9,9,9,0,0,0,1]
```

 

**Constraints:**

	- The number of nodes in each linked list is in the range `[1, 100]`.
	- `0 <= Node.val <= 9`
	- It is guaranteed that the list represents a number that does not have leading zeros.

#### 💡 Revision note

```text
Pattern: Linked list traversal with carry
Key idea: Reverse digit order allows left-to-right addition; carry propagation and dummy node streamline implementation.
Complexity: O(max(m,n)) time / O(max(m,n)) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {

        int carry = 0;
        ListNode fin = new ListNode();
        ListNode res = fin;

        while(l1 != null && l2 != null){
            int v = l1.val + l2.val + carry;
            if(v>9){
                carry = 1;
                v = v%10;
            }else{
                carry = 0;
            }
            res.next = new ListNode(v);
            l1 = l1.next;
            l2 = l2.next;
            res = res.next;
        }

        while(l1 !=null){
            int v = l1.val + carry;
            if(v>9){
                carry = 1;
                v = v%10;
            }else{
                carry = 0;
            }
            res.next = new ListNode(v);
            l1 = l1.next;
            res = res.next;
        }

        while(l2 !=null){
            int v = l2.val + carry;
            if(v>9){
                carry = 1;
                v = v%10;
            }else{
                carry = 0;
            }
            res.next = new ListNode(v);
            l2 = l2.next;
            res = res.next;
        }
        if(carry == 1){
            res.next = new ListNode(1);
            res = res.next;
        }

        return fin.next;
        
    }
}
```

</details>

### 🟡 143. Reorder List

**Medium** · 🏷️ Linked List, Two Pointers, Stack, Recursion · 📅 2025-11-16

#### 📄 Problem

You are given the head of a singly linked-list. The list can be represented as:

```
L_0 → L_1 → … → L_n - 1 → L_n
```

*Reorder the list to be on the following form:*

```
L_0 → L_n → L_1 → L_n - 1 → L_2 → L_n - 2 → …
```

You may not modify the values in the list's nodes. Only nodes themselves may be changed.

 

Example 1:

```
**Input:** head = [1,2,3,4]
**Output:** [1,4,2,3]
```

Example 2:

```
**Input:** head = [1,2,3,4,5]
**Output:** [1,5,2,4,3]
```

 

**Constraints:**

	- The number of nodes in the list is in the range `[1, 5 * 10^4]`.
	- `1 <= Node.val <= 1000`

#### 💡 Revision note

```text
Pattern: Find middle, reverse, merge
Key idea: Reversing the second half enables merging to naturally pair nodes from start and end moving inward.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public void reorderList(ListNode head) {

        ListNode slow = head;
        ListNode fast = head;

        while(fast != null && fast.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }

        ListNode second = reverse(slow.next);
        slow.next = null;

        ListNode first = head;
        while(second != null){
            ListNode temp1 = first.next;
            ListNode temp2 = second.next;

            first.next = second;
            second.next = temp1;


            first = temp1;
            second = temp2;
        }

    }

    private int findlength(ListNode curr){
        int i =0;
        while(curr != null){
            curr = curr.next;
            i++;
        }
        return i;
    }


    private ListNode reverse(ListNode head){

        ListNode prev = null;
        ListNode curr = head;
        ListNode temp;

        while(curr!=null){
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr =temp;
        }
        return prev;


    }
}
```

</details>

### 🔴 25. Reverse Nodes in k-Group

**Hard** · 🏷️ Linked List, Recursion · 📅 2026-03-09

#### 📄 Problem

Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return *the modified list*.

`k` is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of `k` then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

 

Example 1:

```
**Input:** head = [1,2,3,4,5], k = 2
**Output:** [2,1,4,3,5]
```

Example 2:

```
**Input:** head = [1,2,3,4,5], k = 3
**Output:** [3,2,1,4,5]
```

 

**Constraints:**

	- The number of nodes in the list is `n`.
	- `1 <= k <= n <= 5000`
	- `0 <= Node.val <= 1000`

 

**Follow-up:** Can you solve the problem in `O(1)` extra memory space?

#### 💡 Revision note

```text
Pattern: K-group iterative reversal
Key idea: Reverse complete k-node groups through pointer re-linking; preserve incomplete trailing groups.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseKGroup(ListNode head, int k) {

        ListNode curr = head;
        ListNode res = null;
        ListNode fin = null;
        while(curr !=null ){
            ListNode temp1 = new ListNode();
            ListNode temp2 = temp1;
            int i = 0;
            while(i<k && curr!=null){
                temp1.next = curr;
                curr = curr.next;
                temp1 = temp1.next;
                i++;
            }
            temp1.next = null;

            if(res == null){
                res = new ListNode();
                fin = res;
                res.next = reverseNode(temp2.next);
            }else{
                if(i == k){
                    while(i>0){
                        res = res.next;
                        i--;
                    }
                    res.next = reverseNode(temp2.next);
                }else{
                    System.out.println(i);
                    while(k>0){
                        res = res.next;
                        k--;
                    }
                    res.next = temp2.next;
                }
                
            }
        }
                         
        return fin.next;




    }

    private ListNode reverseNode(ListNode node){
        ListNode prev = null;
        ListNode curr = node;
        ListNode temp;

        while(curr != null){
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }
}
```

</details>

---

## Sliding Window (5)

### 🟡 3. Longest Substring Without Repeating Characters

**Medium** · 🏷️ Hash Table, String, Sliding Window · 📅 2025-11-11

#### 📄 Problem

Given a string `s`, find the length of the **longest** **substring** without duplicate characters.

 

Example 1:

```
**Input:** s = "abcabcbb"
**Output:** 3
**Explanation:** The answer is "abc", with the length of 3. Note that `"bca"` and `"cab"` are also correct answers.
```

Example 2:

```
**Input:** s = "bbbbb"
**Output:** 1
**Explanation:** The answer is "b", with the length of 1.
```

Example 3:

```
**Input:** s = "pwwkew"
**Output:** 3
**Explanation:** The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

 

**Constraints:**

	- `0 <= s.length <= 5 * 10^4`
	- `s` consists of English letters, digits, symbols and spaces.

#### 💡 Revision note

```text
Pattern: Sliding window
Key idea: Two pointers with one pass: left never backtracks, so each character is processed at most twice.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        boolean[] vis = new boolean[1000];
        int l = 0;
        int r = 0;
        int n = s.length();
        int ans = 0;
        // s = s.trim();

        if(s.length()== 1){
            return 1;
        }

        while(r<n){

            while(vis[s.charAt(r)] == true){
                vis[s.charAt(l)] = false;
                l++;
            }

            ans = Integer.max(ans, r-l+1);
            vis[s.charAt(r)]=true;
            r++;
        } 
        return ans;
    }
}
```

</details>

### 🟡 424. Longest Repeating Character Replacement

**Medium** · 🏷️ Hash Table, String, Sliding Window · 📅 2026-03-22

#### 📄 Problem

You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return *the length of the longest substring containing the same letter you can get after performing the above operations*.

 

Example 1:

```
**Input:** s = "ABAB", k = 2
**Output:** 4
**Explanation:** Replace the two 'A's with two 'B's or vice versa.
```

Example 2:

```
**Input:** s = "AABABBA", k = 1
**Output:** 4
**Explanation:** Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achieve this answer too.
```

 

**Constraints:**

	- `1 <= s.length <= 10^5`
	- `s` consists of only uppercase English letters.
	- `0 <= k <= s.length`

#### 💡 Revision note

```text
Pattern: Sliding window + hashmap
Key idea: Minimum replacements in window = length - max_frequency; if ≤ k, substring can be uniform.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int characterReplacement(String s, int k) {
        int maxLength = 0;
        int maxCount = 0;
        int start = 0;
        Map<Character, Integer> countMap = new HashMap<>();

        for (int end = 0; end < s.length(); end++) {
            char endChar = s.charAt(end);
            countMap.put(endChar, countMap.getOrDefault(endChar, 0) + 1);
            maxCount = Math.max(maxCount, countMap.get(endChar));

            if (end - start + 1 - maxCount > k) {
                char startChar = s.charAt(start);
                countMap.put(startChar, countMap.get(startChar) - 1);
                start++;
            }

            maxLength = Math.max(maxLength, end - start + 1);
        }

        return maxLength;
    }
}
```

</details>

### 🟡 567. Permutation in String

**Medium** · 🏷️ Hash Table, Two Pointers, String, Sliding Window · 📅 2025-11-12

#### 📄 Problem

Given two strings `s1` and `s2`, return `true` if `s2` contains a permutation of `s1`, or `false` otherwise.

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

 

Example 1:

```
**Input:** s1 = "ab", s2 = "eidbaooo"
**Output:** true
**Explanation:** s2 contains one permutation of s1 ("ba").
```

Example 2:

```
**Input:** s1 = "ab", s2 = "eidboaoo"
**Output:** false
```

 

**Constraints:**

	- `1 <= s1.length, s2.length <= 10^4`
	- `s1` and `s2` consist of lowercase English letters.

#### 💡 Revision note

```text
Pattern: Sliding window with frequency counter
Key idea: Permutations have identical character frequencies; track when a sliding window matches this exact distribution.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        
        int[] charArr = new int[26];

        int dist = 0;

        for(char c : s1.toCharArray()){
            charArr[c-'a']++;
            if(charArr[c-'a']==1){
                dist++;
            }
        }

        int n = s1.length();
        int m = s2.length();

        for(int i = 0;i<m; i++){
            char ch = s2.charAt(i);
            charArr[ch-'a']--;
            if(charArr[ch-'a']==0){
                dist--;
            }

            if(i>=n){
                char cl = s2.charAt(i-n);
                charArr[cl-'a']++;
                if(charArr[cl-'a']==1){
                    dist++;
                }
            }

            if(dist == 0){
                return true;
            }
        }
        return false;
    }
}
```

</details>

### 🟡 2110. Number of Smooth Descent Periods of a Stock

**Medium** · 🏷️ Array, Math, Two Pointers, Dynamic Programming, Sliding Window · 📅 2024-09-17

#### 📄 Problem

You are given an integer array `prices` representing the daily price history of a stock, where `prices[i]` is the stock price on the `i^th` day.

A **smooth descent period** of a stock consists of **one or more contiguous** days such that the price on each day is **lower** than the price on the **preceding day** by **exactly** `1`. The first day of the period is exempted from this rule.

Return *the number of **smooth descent periods***.

 

Example 1:

```
**Input:** prices = [3,2,1,4]
**Output:** 7
**Explanation:** There are 7 smooth descent periods:
[3], [2], [1], [4], [3,2], [2,1], and [3,2,1]
Note that a period with one day is a smooth descent period by the definition.
```

Example 2:

```
**Input:** prices = [8,6,7,7]
**Output:** 4
**Explanation:** There are 4 smooth descent periods: [8], [6], [7], and [7]
Note that [8,6] is not a smooth descent period as 8 - 6 ≠ 1.
```

Example 3:

```
**Input:** prices = [1]
**Output:** 1
**Explanation:** There is 1 smooth descent period: [1]
```

 

**Constraints:**

	- `1 <= prices.length <= 10^5`
	- `1 <= prices[i] <= 10^5`

#### 💡 Revision note

```text
Pattern: Greedy descent streak counting
Key idea: A descent streak of length n yields n*(n+1)/2 valid periods; count each streak's contribution greedily.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public long getDescentPeriods(int[] prices) {
        int end = 0;
        int start =0;
        long res =1;

        for(end = 1; end<prices.length ; end++){
            if(prices[end]==prices[end-1] - 1){
                res = res + end - start + 1;
            }
            else{
                start = end;
                res = res + end - start + 1;
            }
        }
        return res;
    }
}
```

</details>

### 🔴 76. Minimum Window Substring

**Hard** · 🏷️ Hash Table, String, Sliding Window · 📅 2026-03-06

#### 📄 Problem

Given two strings `s` and `t` of lengths `m` and `n` respectively, return *the **minimum window*** ***substring**** of *`s`* such that every character in *`t`* (**including duplicates**) is included in the window*. If there is no such substring, return *the empty string *`""`.

The testcases will be generated such that the answer is **unique**.

 

Example 1:

```
**Input:** s = "ADOBECODEBANC", t = "ABC"
**Output:** "BANC"
**Explanation:** The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
```

Example 2:

```
**Input:** s = "a", t = "a"
**Output:** "a"
**Explanation:** The entire string s is the minimum window.
```

Example 3:

```
**Input:** s = "a", t = "aa"
**Output:** ""
**Explanation:** Both 'a's from t must be included in the window.
Since the largest window of s only has one 'a', return empty string.
```

 

**Constraints:**

	- `m == s.length`
	- `n == t.length`
	- `1 <= m, n <= 10^5`
	- `s` and `t` consist of uppercase and lowercase English letters.

 

**Follow up:** Could you find an algorithm that runs in `O(m + n)` time?

#### 💡 Revision note

```text
Pattern: Sliding window with hashmap
Key idea: Expand right to collect required characters, then shrink left to find the minimum valid window.
Complexity: O(m + n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public String minWindow(String s, String t) {
        int n = s.length();
        int m = t.length();

        Map<Character,Integer> map = new HashMap<>();

        for(int  i =0;i<m;i++){
            map.put(t.charAt(i),map.getOrDefault(t.charAt(i),0)+1);
        }
        m = map.size();

        int l =0;
        int r =0;
        int c =0;
        int min = Integer.MAX_VALUE;
        int initialIndex = -1;
        String res = "";

        while(r<n){
            map.put(s.charAt(r),map.getOrDefault(s.charAt(r),0)-1);
            if(map.get(s.charAt(r)) == 0){
                c++;
            }
            while(c==m){
                if(min > r-l+1){
                    min = r-l+1;
                    res = s.substring(l,r+1);
                }
                if(map.get(s.charAt(l)) == 0){
                    c--;
                }
                map.put(s.charAt(l),map.getOrDefault(s.charAt(l),0)+1);
                l++;
            }
            r++;
        }

        return res;
        
    }
}
```

</details>

---

## Design (4)

### 🟡 155. Min Stack

**Medium** · 🏷️ Stack, Design · 📅 2025-11-02

#### 📄 Problem

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

	- `MinStack()` initializes the stack object.
	- `void push(int value)` pushes the element `value` onto the stack.
	- `void pop()` removes the element on the top of the stack.
	- `int top()` gets the top element of the stack.
	- `int getMin()` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.

 

Example 1:

```
**Input**
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

**Output**
[null,null,null,null,-3,null,0,-2]

**Explanation**
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```

 

**Constraints:**

	- `-2^31 <= val <= 2^31 - 1`
	- Methods `pop`, `top` and `getMin` operations will always be called on **non-empty** stacks.
	- At most `3 * 10^4` calls will be made to `push`, `pop`, `top`, and `getMin`.

#### 💡 Revision note

```text
Pattern: Parallel min stack
Key idea: Synchronize a min stack with main stack: push when value ≤ current min, keeping min stack's top as the current minimum.
Complexity: O(1) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class MinStack {

    Stack<Integer> mainStack = new Stack<>();
    Stack<Integer> minStack = new Stack<>();
    int min = 0;

    public MinStack() {
        
    }
    
    public void push(int val) {
        if(!minStack.isEmpty()){
            if(minStack.peek()>=val){
                minStack.push(val);
                min=val;
            }
        }else{
            minStack.push(val);
            min=val;
        }
        mainStack.push(val);
    }
    
    public void pop() {
        if(!minStack.isEmpty()){
            if(mainStack.peek().equals(minStack.peek())){
                minStack.pop();
            }
        }

        mainStack.pop();
    }
    
    public int top() {
        return mainStack.peek();
    }
    
    public int getMin() {
        // Stack<Integer> minStack = new Stack<>();
        // int min = Integer.MAX_VALUE;
        // while(!mainStack.isEmpty()){
        //     min = Integer.min(min,mainStack.peek());
        //     minStack.push(mainStack.pop());
        // }
        // while(!minStack.isEmpty()){
        //     mainStack.push(minStack.pop());
        // }
        if(!minStack.isEmpty())
            return minStack.peek();
        return -1;

    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```

</details>

### 🟡 355. Design Twitter

**Medium** · 🏷️ Hash Table, Linked List, Design, Heap (Priority Queue) · 📅 2026-03-29

#### 📄 Problem

Design a simplified version of Twitter where users can post tweets, follow/unfollow another user, and is able to see the `10` most recent tweets in the user's news feed.

Implement the `Twitter` class:

	- `Twitter()` Initializes your twitter object.
	- `void postTweet(int userId, int tweetId)` Composes a new tweet with ID `tweetId` by the user `userId`. Each call to this function will be made with a unique `tweetId`.
	- `List<Integer> getNewsFeed(int userId)` Retrieves the `10` most recent tweet IDs in the user's news feed. Each item in the news feed must be posted by users who the user followed or by the user themself. Tweets must be **ordered from most recent to least recent**.
	- `void follow(int followerId, int followeeId)` The user with ID `followerId` started following the user with ID `followeeId`.
	- `void unfollow(int followerId, int followeeId)` The user with ID `followerId` started unfollowing the user with ID `followeeId`.

 

Example 1:

```
**Input**
["Twitter", "postTweet", "getNewsFeed", "follow", "postTweet", "getNewsFeed", "unfollow", "getNewsFeed"]
[[], [1, 5], [1], [1, 2], [2, 6], [1], [1, 2], [1]]
**Output**
[null, null, [5], null, null, [6, 5], null, [5]]

**Explanation**
Twitter twitter = new Twitter();
twitter.postTweet(1, 5); // User 1 posts a new tweet (id = 5).
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 1 tweet id -> [5]. return [5]
twitter.follow(1, 2);    // User 1 follows user 2.
twitter.postTweet(2, 6); // User 2 posts a new tweet (id = 6).
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 2 tweet ids -> [6, 5]. Tweet id 6 should precede tweet id 5 because it is posted after tweet id 5.
twitter.unfollow(1, 2);  // User 1 unfollows user 2.
twitter.getNewsFeed(1);  // User 1's news feed should return a list with 1 tweet id -> [5], since user 1 is no longer following user 2.
```

 

**Constraints:**

	- `1 <= userId, followerId, followeeId <= 500`
	- `0 <= tweetId <= 10^4`
	- All the tweets have **unique** IDs.
	- At most `3 * 10^4` calls will be made to `postTweet`, `getNewsFeed`, `follow`, and `unfollow`.
	- A user cannot follow himself.

#### 💡 Revision note

```text
Pattern: Min-heap for top-K
Key idea: Instead of sorting, use a min-heap to maintain top K items with O(log K) updates per operation.
Complexity: O(followers · log 10) time / O(tweets + followers) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Twitter {

    class Tweet{
        int tweetId;
        int time;

        Tweet(int tweetId, int time){
            this.tweetId = tweetId;
            this.time = time;
        }

        public int getTweetId(){
            return tweetId;
        }
    }

    Map<Integer,List<Tweet>> users;

    public static int time = 0;

    Map<Integer,Set<Integer>> followers;

    public Twitter() {
        users = new HashMap<>();
        followers = new HashMap<>();
    }
    
    public void postTweet(int userId, int tweetId) {
        users.putIfAbsent(userId, new ArrayList<>());
        users.get(userId).add(0,new Tweet(tweetId,time++));
    }
    
    public List<Integer> getNewsFeed(int userId) {

        PriorityQueue<Tweet> q = new PriorityQueue<Tweet>(
            new Comparator<Tweet>(){
                @Override
                public int compare(Tweet t1, Tweet t2 ){
                    return t1.time - t2.time;
                }
            }
        );

        List<Integer> us = new ArrayList<>();
        us.add(userId);
        if(followers.containsKey(userId)){
            us.addAll(followers.get(userId));
        }



        for(Integer u : us){

            if(users.containsKey(u)){
                List<Tweet> tweets = users.get(u);

                for(int i = 0;i<Math.min(10,tweets.size());i++){
                    q.offer(tweets.get(i));
                    if(q.size()>10){
                        q.poll();
                    }
                }
            }
        }

        List<Integer> res = new ArrayList<>();
        while(!q.isEmpty()){
            res.add(0,q.poll().tweetId);
        }

        return res;
    }
    
    public void follow(int followerId, int followeeId) {
        followers.putIfAbsent(followerId,new HashSet<>());
        followers.get(followerId).add(followeeId);
        
    }
    
    public void unfollow(int followerId, int followeeId) {

        if(followers.containsKey(followerId) && followerId != followeeId){
            followers.get(followerId).remove(followeeId);
        }
        
    }
}

/**
 * Your Twitter object will be instantiated and called as such:
 * Twitter obj = new Twitter();
 * obj.postTweet(userId,tweetId);
 * List<Integer> param_2 = obj.getNewsFeed(userId);
 * obj.follow(followerId,followeeId);
 * obj.unfollow(followerId,followeeId);
 */
```

</details>

### 🟡 981. Time Based Key-Value Store

**Medium** · 🏷️ Hash Table, String, Binary Search, Design · 📅 2025-11-09

#### 📄 Problem

Design a time-based key-value data structure that can store multiple values for the same key at different time stamps and retrieve the key's value at a certain timestamp.

Implement the `TimeMap` class:

	- `TimeMap()` Initializes the object of the data structure.
	- `void set(String key, String value, int timestamp)` Stores the key `key` with the value `value` at the given time `timestamp`.
	- `String get(String key, int timestamp)` Returns a value such that `set` was called previously, with `timestamp_prev <= timestamp`. If there are multiple such values, it returns the value associated with the largest `timestamp_prev`. If there are no values, it returns `""`.

 

Example 1:

```
**Input**
["TimeMap", "set", "get", "get", "set", "get", "get"]
[[], ["foo", "bar", 1], ["foo", 1], ["foo", 3], ["foo", "bar2", 4], ["foo", 4], ["foo", 5]]
**Output**
[null, null, "bar", "bar", null, "bar2", "bar2"]

**Explanation**
TimeMap timeMap = new TimeMap();
timeMap.set("foo", "bar", 1);  // store the key "foo" and value "bar" along with timestamp = 1.
timeMap.get("foo", 1);         // return "bar"
timeMap.get("foo", 3);         // return "bar", since there is no value corresponding to foo at timestamp 3 and timestamp 2, then the only value is at timestamp 1 is "bar".
timeMap.set("foo", "bar2", 4); // store the key "foo" and value "bar2" along with timestamp = 4.
timeMap.get("foo", 4);         // return "bar2"
timeMap.get("foo", 5);         // return "bar2"
```

 

**Constraints:**

	- `1 <= key.length, value.length <= 100`
	- `key` and `value` consist of lowercase English letters and digits.
	- `1 <= timestamp <= 10^7`
	- All the timestamps `timestamp` of `set` are strictly increasing.
	- At most `2 * 10^5` calls will be made to `set` and `get`.

#### 💡 Revision note

```text
Pattern: Binary search on sorted timestamps
Key idea: Timestamps always increase, so binary search efficiently finds the largest timestamp ≤ query.
Complexity: set O(1), get O(log n) time / O(m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class TimeMap {

    Map<String,Map<Integer,String>> map = new HashMap<>();
    Map<String,ArrayList<Integer>> prevTime= new HashMap<>();
    public TimeMap() {
        
    }
    
    public void set(String key, String value, int timestamp) {
        ArrayList<Integer> arr = prevTime.getOrDefault(key,new ArrayList<>());
        arr.add(timestamp);
        prevTime.put(key,arr);

            Map<Integer,String> subMap = map.getOrDefault(key,new HashMap<>());
            subMap.put(timestamp,value);
            map.put(key,subMap);
            
    }
    
    public String get(String key, int timestamp) {
        Map<Integer,String> subMap = map.get(key);
        ArrayList<Integer> list = prevTime.get(key);

        if(list == null){
            return "";
        }
        
        int id = getByTimeStamp(list,timestamp);
        if(id == -1){
            return "";
        }
        int v = list.get(id);
        return subMap.get(v);
        
    }

    private int getByTimeStamp(ArrayList<Integer> list, int timestamp){
        int l = 0;
        int h = list.size()-1;
        int r = -1;

        while(l<=h){
            int m = (l+h)/2;
            if(list.get(m)<=timestamp){
                r = m;
                l = m+1;
            }
            else{
                h = m-1;
            }
        }
        return r;
    }
}

/**
 * Your TimeMap object will be instantiated and called as such:
 * TimeMap obj = new TimeMap();
 * obj.set(key,value,timestamp);
 * String param_2 = obj.get(key,timestamp);
 */
```

</details>

### 🔴 297. Serialize and Deserialize Binary Tree

**Hard** · 🏷️ String, Tree, Depth-First Search, Breadth-First Search, Design, Binary Tree · 📅 2026-03-07

#### 📄 Problem

Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

**Clarification:** The input/output format is the same as how LeetCode serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.

 

Example 1:

```
**Input:** root = [1,2,3,null,null,4,5]
**Output:** [1,2,3,null,null,4,5]
```

Example 2:

```
**Input:** root = []
**Output:** []
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[0, 10^4]`.
	- `-1000 <= Node.val <= 1000`

#### 💡 Revision note

```text
Pattern: Level-order serialization
Key idea: Level-order traversal preserves parent-child relationships; null markers allow reconstruction from sequential order.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if(root == null){
            return null;
        }

        StringBuilder str = new StringBuilder();
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);

        while(!q.isEmpty()){
            TreeNode node = q.poll();
            if(node==null){
                str.append("#");
                str.append(" ");
                continue;
            }
            str.append(node.val);
            str.append(" ");
            TreeNode left = node.left;
            TreeNode right = node.right;
            q.add(left);
            q.add(right);
        }
        return str.toString();
        
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data == null){
            return null;
        }
        System.out.println(""+data);

        String[] str = data.split(" ");
        Queue<TreeNode> q = new LinkedList<>();
        TreeNode root = new TreeNode(Integer.parseInt(str[0]));
        q.add(root);
        for(int i = 1;i<str.length; i++){
            TreeNode node = q.poll();
            if(!str[i].equals("#")){
                TreeNode left = new TreeNode(Integer.parseInt(str[i]));
                node.left = left;
                q.add(left);
            }
            i++;
            if(!str[i].equals("#")){
                TreeNode right = new TreeNode(Integer.parseInt(str[i]));
                node.right = right;
                q.add(right);
            }

        }

        return root;
        
    }
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));
```

</details>

---

## Linked List (4)

### 🟢 141. Linked List Cycle

**Easy** · 🏷️ Hash Table, Linked List, Two Pointers · 📅 2025-11-14

#### 📄 Problem

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true`* if there is a cycle in the linked list*. Otherwise, return `false`.

 

Example 1:

```
**Input:** head = [3,2,0,-4], pos = 1
**Output:** true
**Explanation:** There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

Example 2:

```
**Input:** head = [1,2], pos = 0
**Output:** true
**Explanation:** There is a cycle in the linked list, where the tail connects to the 0th node.
```

Example 3:

```
**Input:** head = [1], pos = -1
**Output:** false
**Explanation:** There is no cycle in the linked list.
```

 

**Constraints:**

	- The number of the nodes in the list is in the range `[0, 10^4]`.
	- `-10^5 <= Node.val <= 10^5`
	- `pos` is `-1` or a **valid index** in the linked-list.

 

**Follow up:** Can you solve it using `O(1)` (i.e. constant) memory?

#### 💡 Revision note

```text
Pattern: Slow and Fast Pointers
Key idea: Different-speed pointers must meet if trapped in a cycle, otherwise fast reaches null first.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {

        if(head == null){
            return false;
        }
        ListNode slow = head;
        ListNode fast = head.next;

        while(slow != null && fast != null && fast.next != null){
            if(slow == fast){
                return true;
            }
            slow = slow.next;
            fast = fast.next.next;

        }
        return false;
    }
}
```

</details>

### 🟡 19. Remove Nth Node From End of List

**Medium** · 🏷️ Linked List, Two Pointers · 📅 2025-11-15

#### 📄 Problem

Given the `head` of a linked list, remove the `n^th` node from the end of the list and return its head.

 

Example 1:

```
**Input:** head = [1,2,3,4,5], n = 2
**Output:** [1,2,3,5]
```

Example 2:

```
**Input:** head = [1], n = 1
**Output:** []
```

Example 3:

```
**Input:** head = [1,2], n = 1
**Output:** [1]
```

 

**Constraints:**

	- The number of nodes in the list is `sz`.
	- `1 <= sz <= 30`
	- `0 <= Node.val <= 100`
	- `1 <= n <= sz`

 

**Follow up:** Could you do this in one pass?

#### 💡 Revision note

```text
Pattern: Two-pass traversal
Key idea: Find list length first, then convert "nth from end" to position from start.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode curr = head;
        int k =0;
        while(curr!=null){
            curr = curr.next;
            k++;
        }

        int l = k-n;
        if(l == 0 ){
            return head.next;
        }
        curr = head;
        for(int i =1;i<l;i++){
            curr = curr.next;
        }
        curr.next = curr.next.next;
        return head;
        
        
    }

    private ListNode reverse(ListNode head){

        ListNode curr = head;
        ListNode prev = null;
        ListNode temp;

        while(curr != null){
            temp = curr.next;
            curr.next = prev;
            prev = curr;
            curr = temp;
        }
        return prev;
    }

}
```

</details>

### 🟡 138. Copy List with Random Pointer

**Medium** · 🏷️ Hash Table, Linked List · 📅 2026-03-14

#### 📄 Problem

A linked list of length `n` is given such that each node contains an additional random pointer, which could point to any node in the list, or `null`.

Construct a **deep copy** of the list. The deep copy should consist of exactly `n` **brand new** nodes, where each new node has its value set to the value of its corresponding original node. Both the `next` and `random` pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. **None of the pointers in the new list should point to nodes in the original list**.

For example, if there are two nodes `X` and `Y` in the original list, where `X.random --> Y`, then for the corresponding two nodes `x` and `y` in the copied list, `x.random --> y`.

Return *the head of the copied linked list*.

The linked list is represented in the input/output as a list of `n` nodes. Each node is represented as a pair of `[val, random_index]` where:

	- `val`: an integer representing `Node.val`
	- `random_index`: the index of the node (range from `0` to `n-1`) that the `random` pointer points to, or `null` if it does not point to any node.

Your code will **only** be given the `head` of the original linked list.

 

Example 1:

```
**Input:** head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
**Output:** [[7,null],[13,0],[11,4],[10,2],[1,0]]
```

Example 2:

```
**Input:** head = [[1,1],[2,1]]
**Output:** [[1,1],[2,1]]
```

Example 3:

****

```
**Input:** head = [[3,null],[3,0],[3,null]]
**Output:** [[3,null],[3,0],[3,null]]
```

 

**Constraints:**

	- `0 <= n <= 1000`
	- `-10^4 <= Node.val <= 10^4`
	- `Node.random` is `null` or is pointing to some node in the linked list.

#### 💡 Revision note

```text
Pattern: HashMap node mapping
Key idea: Map original→copy nodes upfront; random pointers resolve instantly via hashmap lookup.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/

class Solution {
    public Node copyRandomList(Node head) {
        if(head == null){
            return null;
        }
        HashMap<Node,Node> map = new HashMap<>();

        Node newHead = new Node(head.val);
        Node newTemp = newHead;
        Node oldHead = head.next;
        map.put(head,newHead);

        while(oldHead != null){
            Node n = new Node(oldHead.val);
            map.put(oldHead,n);
            newTemp.next = n;
            newTemp = newTemp.next;
            oldHead = oldHead.next;
        }

        newTemp = newHead;
        oldHead = head;

        while(oldHead != null){
            newTemp.random = map.get(oldHead.random); 
            newTemp = newTemp.next;
            oldHead = oldHead.next;
        }
        return newHead;

    }
}
```

</details>

### 🟡 3217. Delete Nodes From Linked List Present in Array

**Medium** · 🏷️ Array, Hash Table, Linked List · 📅 2025-03-01

#### 📄 Problem

You are given an array of integers `nums` and the `head` of a linked list. Return the `head` of the modified linked list after **removing** all nodes from the linked list that have a value that exists in `nums`.

 

Example 1:

**Input:** nums = [1,2,3], head = [1,2,3,4,5]

**Output:** [4,5]

**Explanation:**

****

Remove the nodes with values 1, 2, and 3.

Example 2:

**Input:** nums = [1], head = [1,2,1,2,1,2]

**Output:** [2,2,2]

**Explanation:**

Remove the nodes with value 1.

Example 3:

**Input:** nums = [5], head = [1,2,3,4]

**Output:** [1,2,3,4]

**Explanation:**

****

No node has value 5.

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `1 <= nums[i] <= 10^5`
	- All elements in `nums` are unique.
	- The number of nodes in the given list is in the range `[1, 10^5]`.
	- `1 <= Node.val <= 10^5`
	- The input is generated such that there is at least one node in the linked list that has a value not present in `nums`.

#### 💡 Revision note

```text
Pattern: Dummy node + hashset
Key idea: HashSet provides O(1) lookups; dummy node eliminates special-case handling for head deletion.
Complexity: O(n + m) time / O(m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode modifiedList(int[] nums, ListNode head) {
        ListNode pre = new ListNode();
                ListNode res = pre;
        HashSet<Integer> set = new HashSet<>();
        for(int i=0;i<nums.length;i++){
            set.add(nums[i]);
        }
        while(head != null ){
            int a = head.val;
            if(!set.contains(a)){
                
                pre.next = head;

                pre = pre.next;

            }
            head = head.next;
            pre.next = null;

        }
        return res.next;
    }
}
```

</details>

---

## Sorting (4)

### 🟢 217. Contains Duplicate

**Easy** · 🏷️ Array, Hash Table, Sorting · 📅 2025-10-31

#### 📄 Problem

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

 

Example 1:

**Input:** nums = [1,2,3,1]

**Output:** true

**Explanation:**

The element 1 occurs at the indices 0 and 3.

Example 2:

**Input:** nums = [1,2,3,4]

**Output:** false

**Explanation:**

All elements are distinct.

Example 3:

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]

**Output:** true

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `-10^9 <= nums[i] <= 10^9`

#### 💡 Revision note

```text
Pattern: Hash Set
Key idea: Set stores only unique values; comparing set size to array length identifies duplicates.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = Arrays.stream(nums)
                            .boxed()
                            .collect(Collectors.toSet());
        return set.size()!=nums.length;
    }
}
```

</details>

### 🟢 242. Valid Anagram

**Easy** · 🏷️ Hash Table, String, Sorting · 📅 2025-10-31

#### 📄 Problem

Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

 

Example 1:

**Input:** s = "anagram", t = "nagaram"

**Output:** true

Example 2:

**Input:** s = "rat", t = "car"

**Output:** false

 

**Constraints:**

	- `1 <= s.length, t.length <= 5 * 10^4`
	- `s` and `t` consist of lowercase English letters.

 

**Follow up:** What if the inputs contain Unicode characters? How would you adapt your solution to such a case?

#### 💡 Revision note

```text
Pattern: Sort and compare
Key idea: Two strings are anagrams iff sorting produces the same character sequence.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] s1 = s.toCharArray();
        Arrays.sort(s1);
        s = String.valueOf(s1);

        char[] s2 = t.toCharArray();
        Arrays.sort(s2);
        t = String.valueOf(s2);

        return s.equals(t);

    }
}
```

</details>

### 🟡 15. 3Sum

**Medium** · 🏷️ Array, Two Pointers, Sorting · 📅 2025-11-04

#### 📄 Problem

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

 

Example 1:

```
**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]
**Explanation:** 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

Example 2:

```
**Input:** nums = [0,1,1]
**Output:** []
**Explanation:** The only possible triplet does not sum up to 0.
```

Example 3:

```
**Input:** nums = [0,0,0]
**Output:** [[0,0,0]]
**Explanation:** The only possible triplet sums up to 0.
```

 

**Constraints:**

	- `3 <= nums.length <= 3000`
	- `-10^5 <= nums[i] <= 10^5`

#### 💡 Revision note

```text
Pattern: Nested loop with HashSet
Key idea: Fix first element, reduce to 2Sum by checking if complement exists in HashSet.
Complexity: O(n²) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Set<List<Integer>> set = new HashSet<>();
        int n = nums.length;
        for(int i = 0 ;i<n;i++){
            Set<Integer> subSet = new HashSet<>();
            for(int j = i+1;j<n;j++){
                int com = -nums[i]-nums[j];
                if(subSet.contains(com)){
                    List<Integer> sub = Arrays.asList(com,nums[i],nums[j]);
                    Collections.sort(sub);
                    set.add(sub);
                }
                subSet.add(nums[j]);
            }
        }
        return new ArrayList<>(set);
    }
}
```

</details>

### 🟡 49. Group Anagrams

**Medium** · 🏷️ Array, Hash Table, String, Sorting · 📅 2025-10-29

#### 📄 Problem

Given an array of strings `strs`, group the anagrams together. You can return the answer in **any order**.

 

Example 1:

**Input:** strs = ["eat","tea","tan","ate","nat","bat"]

**Output:** [["bat"],["nat","tan"],["ate","eat","tea"]]

**Explanation:**

	- There is no string in strs that can be rearranged to form `"bat"`.
	- The strings `"nat"` and `"tan"` are anagrams as they can be rearranged to form each other.
	- The strings `"ate"`, `"eat"`, and `"tea"` are anagrams as they can be rearranged to form each other.

Example 2:

**Input:** strs = [""]

**Output:** [[""]]

Example 3:

**Input:** strs = ["a"]

**Output:** [["a"]]

 

**Constraints:**

	- `1 <= strs.length <= 10^4`
	- `0 <= strs[i].length <= 100`
	- `strs[i]` consists of lowercase English letters.

#### 💡 Revision note

```text
Pattern: Sorting + HashMap
Key idea: All anagrams contain the same characters, so sorting them produces identical keys for grouping.
Complexity: O(n * k log k) time / O(n * k) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        
        List<List<String>> list = new ArrayList<>();
        Map<String,List<String>> map = new HashMap<>();
        for(String str: strs){
            char[] ch = str.toCharArray();
            Arrays.sort(ch);
            String strKey = String.valueOf(ch);
            if(!map.containsKey(strKey)){
                map.put(strKey,new ArrayList<>());
            }
            map.get(strKey).add(str);
        }
         return new ArrayList<>(map.values());
    }
}
```

</details>

---

## String (4)

### 🟢 58. Length of Last Word

**Easy** · 🏷️ String · 📅 2026-07-13

#### 📄 Problem

Given a string `s` consisting of words and spaces, return *the length of the **last** word in the string.*

A **word** is a maximal substring consisting of non-space characters only.

 

Example 1:

```
**Input:** s = "Hello World"
**Output:** 5
**Explanation:** The last word is "World" with length 5.
```

Example 2:

```
**Input:** s = "   fly me   to   the moon  "
**Output:** 4
**Explanation:** The last word is "moon" with length 4.
```

Example 3:

```
**Input:** s = "luffy is still joyboy"
**Output:** 6
**Explanation:** The last word is "joyboy" with length 6.
```

 

**Constraints:**

	- `1 <= s.length <= 10^4`
	- `s` consists of only English letters and spaces `' '`.
	- There will be at least one word in `s`.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int lengthOfLastWord(String s) {

        s = s.trim();

        String[] str = s.split(" ");
       int n = str.length;
       System.out.println(str[n-1]);
        
        return str[n-1].length();
        
    }
}
```

</details>

### 🟢 2678. Number of Senior Citizens

**Easy** · 🏷️ Array, String · 📅 2026-07-13

#### 📄 Problem

You are given a **0-indexed** array of strings `details`. Each element of `details` provides information about a given passenger compressed into a string of length `15`. The system is such that:

	- The first ten characters consist of the phone number of passengers.
	- The next character denotes the gender of the person.
	- The following two characters are used to indicate the age of the person.
	- The last two characters determine the seat allotted to that person.

Return *the number of passengers who are **strictly ****more than 60 years old**.*

 

Example 1:

```
**Input:** details = ["7868190130M7522","5303914400F9211","9273338290F4010"]
**Output:** 2
**Explanation:** The passengers at indices 0, 1, and 2 have ages 75, 92, and 40. Thus, there are 2 people who are over 60 years old.
```

Example 2:

```
**Input:** details = ["1313579440F2036","2921522980M5644"]
**Output:** 0
**Explanation:** None of the passengers are older than 60.
```

 

**Constraints:**

	- `1 <= details.length <= 100`
	- `details[i].length == 15`
	- `details[i] consists of digits from '0' to '9'.`
	- `details[i][10] is either 'M' or 'F' or 'O'.`
	- The phone numbers and seat numbers of the passengers are distinct.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int countSeniors(String[] details) {

        int n = details.length;
        int ans =0;
        for(int i=0; i<n; i++){
            String s = details[i];
            char[] ch = s.toCharArray();
            int j = ch[11]-48;
            int k = ch[12]-48;
            int val = j*10 + k;
            if(val > 60){
                ans++;
            }
            // System.out.println(j);
            //  System.out.println(k);
            //   System.out.println("\n");
        }

        return ans;
        
    }
}
```

</details>

### 🟢 3110. Score of a String

**Easy** · 🏷️ String · 📅 2026-07-13

#### 📄 Problem

You are given a string `s`. The **score** of a string is defined as the sum of the absolute difference between the **ASCII** values of adjacent characters.

Return the **score** of* *`s`.

 

Example 1:

**Input:** s = "hello"

**Output:** 13

**Explanation:**

The **ASCII** values of the characters in `s` are: `'h' = 104`, `'e' = 101`, `'l' = 108`, `'o' = 111`. So, the score of `s` would be `|104 - 101| + |101 - 108| + |108 - 108| + |108 - 111| = 3 + 7 + 0 + 3 = 13`.

Example 2:

**Input:** s = "zaz"

**Output:** 50

**Explanation:**

The **ASCII** values of the characters in `s` are: `'z' = 122`, `'a' = 97`. So, the score of `s` would be `|122 - 97| + |97 - 122| = 25 + 25 = 50`.

 

**Constraints:**

	- `2 <= s.length <= 100`
	- `s` consists only of lowercase English letters.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int scoreOfString(String s) {

        char[] ch = s.toCharArray();

        int n = ch.length;
        int ans = 0;
        for(int i=0 ; i<n-1; i++){
            ans = ans + Math.abs(ch[i]-ch[i+1]);
        }
        return ans;
        
    }
}
```

</details>

### 🟡 3163. String Compression III

**Medium** · 🏷️ String · 📅 2024-09-21

#### 📄 Problem

Given a string `word`, compress it using the following algorithm:

	- Begin with an empty string `comp`. While `word` is **not** empty, use the following operation:

	

		Remove a maximum length prefix of `word` made of a *single character* `c` repeating **at most** 9 times.
		- Append the length of the prefix followed by `c` to `comp`.
	

	

Return the string `comp`.

 

Example 1:

**Input:** word = "abcde"

**Output:** "1a1b1c1d1e"

**Explanation:**

Initially, `comp = ""`. Apply the operation 5 times, choosing `"a"`, `"b"`, `"c"`, `"d"`, and `"e"` as the prefix in each operation.

For each prefix, append `"1"` followed by the character to `comp`.

Example 2:

**Input:** word = "aaaaaaaaaaaaaabb"

**Output:** "9a5a2b"

**Explanation:**

Initially, `comp = ""`. Apply the operation 3 times, choosing `"aaaaaaaaa"`, `"aaaaa"`, and `"bb"` as the prefix in each operation.

	- For prefix `"aaaaaaaaa"`, append `"9"` followed by `"a"` to `comp`.
	- For prefix `"aaaaa"`, append `"5"` followed by `"a"` to `comp`.
	- For prefix `"bb"`, append `"2"` followed by `"b"` to `comp`.

 

**Constraints:**

	- `1 <= word.length <= 2 * 10^5`
	- `word` consists only of lowercase English letters.

#### 💡 Revision note

```text
Pattern: Single pass grouping
Key idea: Groups of identical characters are independent; emit each immediately upon character change or reaching 9, solving in one pass.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public String compressedString(String word) {
        String comp = "";
        int len = word.length();
        int j =1;
        if(len == 1){
            return 1+word;
        }
        for(int i=0;i<len-1;i++){
            if(word.charAt(i) == word.charAt(i+1) && j<9){
                j++;
            }
            else {
                comp = comp+j+word.charAt(i);
                j=1;
            }
        }
        if(word.charAt(len-1) == word.charAt(len-2)){
            comp = comp+j+word.charAt(len-1);
        }else{
            comp = comp+1+word.charAt(len-1);
        }
        return comp;
        
    }
}
```

</details>

---

## Trie (4)

### 🟢 14. Longest Common Prefix

**Easy** · 🏷️ Array, String, Trie · 📅 2026-07-14

#### 📄 Problem

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

 

Example 1:

```
**Input:** strs = ["flower","flow","flight"]
**Output:** "fl"
```

Example 2:

```
**Input:** strs = ["dog","racecar","car"]
**Output:** ""
**Explanation:** There is no common prefix among the input strings.
```

 

**Constraints:**

	- `1 <= strs.length <= 200`
	- `0 <= strs[i].length <= 200`
	- `strs[i]` consists of only lowercase English letters if it is non-empty.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {

        if(strs == null || strs.length == 0){
            return "";
        }

        String prefix = strs[0];

        for(int i=1; i<strs.length; i++){
            while(!strs[i].startsWith(prefix)){
                prefix = prefix.substring(0,prefix.length()-1);
                if(prefix.length() == 0){
                    break;
                }
            }
        }
        return prefix;
        
    }
}


```

</details>

### 🟡 208. Implement Trie (Prefix Tree)

**Medium** · 🏷️ Hash Table, String, Design, Trie · 📅 2026-03-17

#### 📄 Problem

A **trie** (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

	- `Trie()` Initializes the trie object.
	- `void insert(String word)` Inserts the string `word` into the trie.
	- `boolean search(String word)` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and `false` otherwise.
	- `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.

 

Example 1:

```
**Input**
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]
**Output**
[null, null, true, false, true, null, true]

**Explanation**
Trie trie = new Trie();
trie.insert("apple");
trie.search("apple");   // return True
trie.search("app");     // return False
trie.startsWith("app"); // return True
trie.insert("app");
trie.search("app");     // return True
```

 

**Constraints:**

	- `1 <= word.length, prefix.length <= 2000`
	- `word` and `prefix` consist only of lowercase English letters.
	- At most `3 * 10^4` calls **in total** will be made to `insert`, `search`, and `startsWith`.

#### 💡 Revision note

```text
Pattern: Trie
Key idea: Hierarchical character storage enables fast prefix and word lookup by traversing one path per query, not searching all stored strings.
Complexity: O(m) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Node{

    Node[] item = new Node[26];
    boolean flag = false;

    boolean containsKey(char ch){
        return (item[ch -'a'] != null);
    }

    void put(char ch, Node node){
        item[ch-'a']=node;
    }

    Node getNode(char ch){
        return item[ch-'a'];
    }
    
    boolean getFlag(){
        return flag;
    }



}



class Trie {

    private static Node root;

    public Trie() {
        root = new Node();
        
    }
    
    public void insert(String word) {

        Node curr = root;

        for(int i =0; i<word.length(); i++){
            char ch = word.charAt(i);
            if(!curr.containsKey(ch)){
                curr.put(ch,new Node());
            }
            curr = curr.getNode(ch);
        }
        curr.flag = true;
        
    }
    
    public boolean search(String word) {

        Node curr = root;

        for(int i =0;i<word.length();i++){
            char ch = word.charAt(i);
            if(!curr.containsKey(ch)){
                return false;
            }
            curr = curr.getNode(ch);
        }
        return curr.flag;
        
    }
    
    public boolean startsWith(String word) {
        Node curr = root;

        for(int i =0;i<word.length();i++){
            char ch = word.charAt(i);
            if(!curr.containsKey(ch)){
                return false;
            }
            curr = curr.getNode(ch);
        }
        return true;
        
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```

</details>

### 🟡 211. Design Add and Search Words Data Structure

**Medium** · 🏷️ String, Depth-First Search, Design, Trie · 📅 2026-03-19

#### 📄 Problem

Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the `WordDictionary` class:

	- `WordDictionary()` Initializes the object.
	- `void addWord(word)` Adds `word` to the data structure, it can be matched later.
	- `bool search(word)` Returns `true` if there is any string in the data structure that matches `word` or `false` otherwise. `word` may contain dots `'.'` where dots can be matched with any letter.

 

Example:

```
**Input**
["WordDictionary","addWord","addWord","addWord","search","search","search","search"]
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]
**Output**
[null,null,null,null,false,true,true,true]

**Explanation**
WordDictionary wordDictionary = new WordDictionary();
wordDictionary.addWord("bad");
wordDictionary.addWord("dad");
wordDictionary.addWord("mad");
wordDictionary.search("pad"); // return False
wordDictionary.search("bad"); // return True
wordDictionary.search(".ad"); // return True
wordDictionary.search("b.."); // return True
```

 

**Constraints:**

	- `1 <= word.length <= 25`
	- `word` in `addWord` consists of lowercase English letters.
	- `word` in `search` consist of `'.'` or lowercase English letters.
	- There will be at most `2` dots in `word` for `search` queries.
	- At most `10^4` calls will be made to `addWord` and `search`.

#### 💡 Revision note

```text
Pattern: Trie with wildcard DFS
Key idea: Trie stores all words by prefix; DFS with backtracking explores 26 branches at each wildcard to find matches.
Complexity: O(m) addWord / O(26^d × m) search where d ≤ 2; O(N×m) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Node{

    Node[] item = new Node[26];
    boolean flag = false;

    boolean containsKey(char ch){
        return (item[ch-'a'] != null);
    }

    void setNode(char ch, Node node){
        item[ch-'a']=node;
    }

    void setTrue(){
        flag=true;
    }

    Node getNode(char ch){
        return item[ch-'a'];
    }

    boolean getFlag(){
        return flag;
    }
}


class WordDictionary {

    private static Node root;

    public WordDictionary() {
        root = new Node();
    }
    
    public void addWord(String word) {
        Node curr = root;
        for(int i=0;i<word.length();i++){
            char ch = word.charAt(i);
            if(!curr.containsKey(ch)){
                curr.setNode(ch,new Node());
            }
            curr = curr.getNode(ch);
        }

        curr.setTrue();

    }
    
    public boolean search(String word) {
    
        return dfs(0,word,root);
    }

    private boolean dfs(int i , String word, Node node){
        if( i == word.length()){
            return node.getFlag();
        }

        char ch = word.charAt(i);
        if(ch != '.'){
            if(!node.containsKey(ch)){
                return false;
            }
            return dfs(i+1,word,node.getNode(ch));
        }

        for(int j = 0;j<26;j++){
            if(node.item[j]!=null){
                if(dfs(i+1,word,node.item[j])){
                    return true;
                }
            }
        }
        return false;
    }
}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary obj = new WordDictionary();
 * obj.addWord(word);
 * boolean param_2 = obj.search(word);
 */
```

</details>

### 🔴 212. Word Search II

**Hard** · 🏷️ Array, String, Backtracking, Trie, Matrix · 📅 2026-03-21

#### 📄 Problem

Given an `m x n` `board` of characters and a list of strings `words`, return *all words on the board*.

Each word must be constructed from letters of sequentially adjacent cells, where **adjacent cells** are horizontally or vertically neighboring. The same letter cell may not be used more than once in a word.

 

Example 1:

```
**Input:** board = [["o","a","a","n"],["e","t","a","e"],["i","h","k","r"],["i","f","l","v"]], words = ["oath","pea","eat","rain"]
**Output:** ["eat","oath"]
```

Example 2:

```
**Input:** board = [["a","b"],["c","d"]], words = ["abcb"]
**Output:** []
```

 

**Constraints:**

	- `m == board.length`
	- `n == board[i].length`
	- `1 <= m, n <= 12`
	- `board[i][j]` is a lowercase English letter.
	- `1 <= words.length <= 3 * 10^4`
	- `1 <= words[i].length <= 10`
	- `words[i]` consists of lowercase English letters.
	- All the strings of `words` are unique.

#### 💡 Revision note

```text
Pattern: Trie + DFS Backtracking
Key idea: Trie prunes invalid prefixes; DFS with backtracking exhaustively explores valid word paths.
Complexity: O(m*n*4^L) time / O(m*n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Node{
    Node[] item = new Node[26];
    String word = null;

    boolean containsKey(char ch){
        return (item[ch-'a'] != null);
    }

    void addNode(char ch, Node node){
        item[ch-'a'] = node;
    }

    Node getNode(char ch){
        return item[ch-'a'];
    }

    void setWord(String word){
        this.word = word;
    }
    
}

class Trie{

    public  Node root;

    Trie(){
        root = new Node();
    }

    void addWord(String word){
        Node curr = root;
        for(int i=0 ; i<word.length() ; i++){
            char ch = word.charAt(i);
            if(!curr.containsKey(ch)){
                curr.addNode(ch,new Node());
            }
            curr = curr.getNode(ch);
        }
        curr.setWord(word);
    }
}

class Solution {

    int[] rr = {0,0,1,-1};
    int[] cc = {-1,1,0,0};

    public List<String> findWords(char[][] board, String[] words) {

        Trie trie = new Trie();
        for(int i = 0; i<words.length; i++){
            trie.addWord(words[i]);
        }
        int n = board.length;
        int m = board[0].length;
        boolean[][] vis = new boolean[n][m];
        List<String> res= new ArrayList<>();

        for(int i=0;i<n;i++){
            for(int j = 0;j<m;j++){
                dfs(i,j,board,vis,res,trie.root);
            }
        }

        return res;
    }

    private void dfs(int i , int j ,char[][] board, boolean[][] vis, List<String>res, Node node){

        if (i < 0 || j < 0 || i >= board.length || j >= board[0].length || vis[i][j]) {
            return;
        }

        

        char ch = board[i][j];

        if(!node.containsKey(ch)){
            return;
        }
         vis[i][j]= true;
        node = node.getNode(ch);
        if(node.word!=null){
            res.add(node.word);
            node.setWord(null);
        }

        for(int k=0;k<4;k++){
            int idx = rr[k]+i;
            int idy = cc[k]+j;
            dfs(idx,idy,board,vis,res,node);

        }
        vis[i][j]= false;

    }
}
```

</details>

---

## Two Pointers (4)

### 🟢 27. Remove Element

**Easy** · 🏷️ Array, Two Pointers · 📅 2026-07-17

#### 📄 Problem

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` **in-place**. The order of the elements may be changed. Then return *the number of elements in *`nums`* which are not equal to *`val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

	- Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
	- Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be **accepted**.

 

Example 1:

```
**Input:** nums = [3,2,2,3], val = 3
**Output:** 2, nums = [2,2,_,_]
**Explanation:** Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

Example 2:

```
**Input:** nums = [0,1,2,2,3,0,4,2], val = 2
**Output:** 5, nums = [0,1,4,0,3,_,_,_]
**Explanation:** Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

 

**Constraints:**

	- `0 <= nums.length <= 100`
	- `0 <= nums[i] <= 50`
	- `0 <= val <= 100`

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int removeElement(int[] nums, int val) {

        int n = nums.length;
        int i =0;
        int j = n-1;
        int ans =0;
        while(i<=j){
            if(val == nums[i]){
                while(j>i && val == nums[j]){
                    j--;
                }
                if (i == j) break;
                swap(nums,i,j);
                j--;
            }
            i++;
        }
        return i;
    }
    private void swap(int[] nums , int i ,int j){
            int temp = nums[i];
            nums[i]=nums[j];
            nums[j]=temp;
    }
}
```

</details>

### 🟢 125. Valid Palindrome

**Easy** · 🏷️ Two Pointers, String · 📅 2026-02-28

#### 📄 Problem

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true`* if it is a **palindrome**, or *`false`* otherwise*.

 

Example 1:

```
**Input:** s = "A man, a plan, a canal: Panama"
**Output:** true
**Explanation:** "amanaplanacanalpanama" is a palindrome.
```

Example 2:

```
**Input:** s = "race a car"
**Output:** false
**Explanation:** "raceacar" is not a palindrome.
```

Example 3:

```
**Input:** s = " "
**Output:** true
**Explanation:** s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

 

**Constraints:**

	- `1 <= s.length <= 2 * 10^5`
	- `s` consists only of printable ASCII characters.

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: After filtering non-alphanumeric chars, comparing from both ends inward checks if the cleaned string is symmetric.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        s = s.replaceAll("[^a-z0-9]","");
        if(s.isEmpty()){
            return true;
        }

        System.out.println(s);

        int l =0;
        int r = s.length()-1;
        while(l<=r){
            if(s.charAt(l)!=s.charAt(r)){
                return false;
            }
            l++;
            r--;
        }
        return true;
    }
}
```

</details>

### 🟢 392. Is Subsequence

**Easy** · 🏷️ Two Pointers, String, Dynamic Programming · 📅 2025-08-31

#### 📄 Problem

Given two strings `s` and `t`, return `true`* if *`s`* is a **subsequence** of *`t`*, or *`false`* otherwise*.

A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).

 

Example 1:

```
**Input:** s = "abc", t = "ahbgdc"
**Output:** true
```
Example 2:

```
**Input:** s = "axc", t = "ahbgdc"
**Output:** false
```

 

**Constraints:**

	- `0 <= s.length <= 100`
	- `0 <= t.length <= 10^4`
	- `s` and `t` consist only of lowercase English letters.

 

**Follow up:** Suppose there are lots of incoming `s`, say `s_1, s_2, ..., s_k` where `k >= 10^9`, and you want to check one by one to see if `t` has its subsequence. In this scenario, how would you change your code?

#### 💡 Revision note

```text
Pattern: Two pointers
Key idea: Greedily match each character of s with its earliest occurrence in t, preserving order.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int i = 0;int j = 0;
        while(j<s.length() && i<t.length()){
            if(s.charAt(j) == t.charAt(i)){
                j++;
            }
            i++;
        }
        return j == s.length();
        
    }
   
   
}
```

</details>

### 🟡 5. Longest Palindromic Substring

**Medium** · 🏷️ Two Pointers, String, Dynamic Programming · 📅 2026-02-02

#### 📄 Problem

Given a string `s`, return *the longest* *palindromic* *substring* in `s`.

 

Example 1:

```
**Input:** s = "babad"
**Output:** "bab"
**Explanation:** "aba" is also a valid answer.
```

Example 2:

```
**Input:** s = "cbbd"
**Output:** "bb"
```

 

**Constraints:**

	- `1 <= s.length <= 1000`
	- `s` consist of only digits and English letters.

#### 💡 Revision note

```text
Pattern: Expand around center
Key idea: Every palindrome has a center; expand from each position to find the longest one.
Complexity: O(n²) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public String longestPalindrome(String s) {

        int first = 0;
        int second = 1;
        int maxlen = 1;

        for(int i = 0; i<s.length();i++){

            // odd palindrome 
            int j = i;
            int k = i;
            while(j>=0 && k < s.length() && s.charAt(j) == s.charAt(k)){

                if(k-j+1 > maxlen){
                    first = j;
                    second = k+1;
                    maxlen = k-j+1;
                }
                j--;
                k++;
            }

            //even length
             j = i;
             k = i+1;
            while(j>=0 && k < s.length() && s.charAt(j) == s.charAt(k)){

                if(k-j+1 > maxlen){
                    first = j;
                    second = k+1;
                    maxlen = k-j+1;
                }
                j--;
                k++;
            }
        }
        return s.substring(first,second);
    }
}
```

</details>

---

## Union-Find (4)

### 🟡 128. Longest Consecutive Sequence

**Medium** · 🏷️ Array, Hash Table, Union-Find · 📅 2025-11-11

#### 📄 Problem

Given an unsorted array of integers `nums`, return *the length of the longest consecutive elements sequence.*

You must write an algorithm that runs in `O(n)` time.

 

Example 1:

```
**Input:** nums = [100,4,200,1,3,2]
**Output:** 4
**Explanation:** The longest consecutive elements sequence is `[1, 2, 3, 4]`. Therefore its length is 4.
```

Example 2:

```
**Input:** nums = [0,3,7,2,5,8,4,6,0,1]
**Output:** 9
```

Example 3:

```
**Input:** nums = [1,0,1,2]
**Output:** 3
```

 

**Constraints:**

	- `0 <= nums.length <= 10^5`
	- `-10^9 <= nums[i] <= 10^9`

#### 💡 Revision note

```text
Pattern: HashSet with start detection
Key idea: Hash-based O(1) predecessor checks prevent redundant traversals; each sequence starts from just one element.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        int n = nums.length;
        Set<Integer> set = new HashSet<>();
        for(int i : nums){
            set.add(i);
        }
        int ans = 0;
        for(int num : set){
            if(!set.contains(num-1)){
                int curr = num;
                int s = 1;
                while(set.contains(curr+1)){
                    s++;
                    curr++;
                }

                ans = Integer.max(s,ans);


            }
        }
        return ans;

    }
}
```

</details>

### 🟡 130. Surrounded Regions

**Medium** · 🏷️ Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix · 📅 2026-04-03

#### 📄 Problem

You are given an `m x n` matrix `board` containing **letters** `'X'` and `'O'`, **capture regions** that are **surrounded**:

	- **Connect**: A cell is connected to adjacent cells horizontally or vertically.
	- **Region**: To form a region **connect every** `'O'` cell.
	- **Surround**: A region is surrounded if none of the `'O'` cells in that region are on the edge of the board. Such regions are **completely enclosed **by `'X'` cells.

To capture a **surrounded region**, replace all `'O'`s with `'X'`s **in-place** within the original board. You do not need to return anything.

 

Example 1:

**Input:** board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]

**Output:** [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]

**Explanation:**

In the above diagram, the bottom region is not captured because it is on the edge of the board and cannot be surrounded.

Example 2:

**Input:** board = [["X"]]

**Output:** [["X"]]

 

**Constraints:**

	- `m == board.length`
	- `n == board[i].length`
	- `1 <= m, n <= 200`
	- `board[i][j]` is `'X'` or `'O'`.

#### 💡 Revision note

```text
Pattern: Border-first DFS
Key idea: Mark O's touching the edge as safe; anything not reachable from the edge is surrounded.
Complexity: O(m*n) time / O(m*n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

    int[] rr = {0,0,-1,1};
    int[] cc = {-1,1,0,0};

    public void solve(char[][] board) {

        int n = board.length;
        int m = board[0].length;

        int[][] vis = new int[n][m];
        
        for(int j=0; j<m; j++){
            if(board[0][j]=='O'){
                dfs(0,j,vis,board,n,m);
            }
        }

        for(int i=0; i<n; i++){
            if(board[i][0]=='O'){
                dfs(i,0,vis,board,n,m);
            }
        }

        for(int j=0; j<m; j++){
            if(board[n-1][j]=='O'){
                dfs(n-1,j,vis,board,n,m);
            }
        }

        for(int i=0; i<n; i++){
            if(board[i][m-1]=='O'){
                dfs(i,m-1,vis,board,n,m);
            }
        }

        for(int i=0;i<n;i++){
            for(int j = 0;j<m;j++){
                if(board[i][j]=='T'){
                    board[i][j]='O';
                }else{
                    board[i][j]='X';
                }
            }
        }



    }

    void dfs(int i, int j , int[][] vis, char[][] board, int n, int m){

        if(i<0 || j<0 || i>=n || j>=m || vis[i][j]==1){
            return;
        }
        vis[i][j]=1;
        board[i][j]='T';

        for(int k = 0;k<4;k++){
            int idx = rr[k]+i;
            int idy = cc[k]+j;

            if(idx>=0 && idy>=0 && idx<n && idy<m && board[idx][idy]=='O'){
                dfs(idx,idy,vis,board,n,m);
            }
        }


    }
}
```

</details>

### 🟡 200. Number of Islands

**Medium** · 🏷️ Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix · 📅 2026-03-31

#### 📄 Problem

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return *the number of islands*.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

 

Example 1:

```
**Input:** grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
**Output:** 1
```

Example 2:

```
**Input:** grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
**Output:** 3
```

 

**Constraints:**

	- `m == grid.length`
	- `n == grid[i].length`
	- `1 <= m, n <= 300`
	- `grid[i][j]` is `'0'` or `'1'`.

#### 💡 Revision note

```text
Pattern: DFS for connected components
Key idea: Each unvisited '1' starts a DFS exploring the entire island; each DFS counts as one island.
Complexity: O(m × n) time / O(m × n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

    int[] cc = {0,0,-1,1};
    int[] rr = {-1,1,0,0};
    public int numIslands(char[][] grid) {

        int n = grid.length;
        int m = grid[0].length;
        int[][] vis = new int[n][m];

        int ans = 0;

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(grid[i][j]=='1' && vis[i][j] == 0){
                    dfs(i,j,vis,grid,n,m);
                    ans++;
                }
            }
        }
        return ans;
    }

    private void dfs(int i, int j ,int[][] vis, char[][] grid,int n ,int m){

    
        vis[i][j]=1;

            for(int k=0; k<4;k++){
                int idx = cc[k]+ i;
                int idy = rr[k] + j;
                if(idx>=0 && idx<n && idy>=0 && idy<m){
                    if(grid[idx][idy]=='1' && vis[idx][idy] == 0)
                        dfs(idx,idy,vis,grid,n,m);
                }
            }        
    }
}
```

</details>

### 🟡 695. Max Area of Island

**Medium** · 🏷️ Array, Depth-First Search, Breadth-First Search, Union-Find, Matrix · 📅 2026-03-31

#### 📄 Problem

You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

The **area** of an island is the number of cells with a value `1` in the island.

Return *the maximum **area** of an island in *`grid`. If there is no island, return `0`.

 

Example 1:

```
**Input:** grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
**Output:** 6
**Explanation:** The answer is not 11, because the island must be connected 4-directionally.
```

Example 2:

```
**Input:** grid = [[0,0,0,0,0,0,0,0]]
**Output:** 0
```

 

**Constraints:**

	- `m == grid.length`
	- `n == grid[i].length`
	- `1 <= m, n <= 50`
	- `grid[i][j]` is either `0` or `1`.

#### 💡 Revision note

```text
Pattern: Connected components DFS
Key idea: DFS from each unvisited land cell explores all 4-directionally connected cells, counting complete island areas.
Complexity: O(m × n) time / O(m × n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {

    int[] cc = {0,0,-1,1};
    int[] rr = {-1,1,0,0};
    public int maxAreaOfIsland(int[][] grid) {

        int n = grid.length;
        int m = grid[0].length;
        int[][] vis = new int[n][m];

        int ans = 0;

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(grid[i][j]==1 && vis[i][j] == 0){
                    ans = Integer.max(dfs(i,j,vis,grid,n,m),ans);
                }
            }
        }
        return ans;
    }

    private int dfs(int i, int j ,int[][] vis, int[][] grid,int n ,int m){    

        int a = 1;
        vis[i][j]=1;

            for(int k=0; k<4;k++){
                int idx = cc[k]+ i;
                int idy = rr[k] + j;
                if(idx>=0 && idx<n && idy>=0 && idy<m){
                    if(grid[idx][idy]==1 && vis[idx][idy] == 0)
                        a = a+dfs(idx,idy,vis,grid,n,m);
                }
            }
        return a;
        
    }
}
```

</details>

---

## Binary Search Tree (3)

### 🟡 98. Validate Binary Search Tree

**Medium** · 🏷️ Tree, Depth-First Search, Binary Search Tree, Binary Tree · 📅 2025-11-23

#### 📄 Problem

Given the `root` of a binary tree, *determine if it is a valid binary search tree (BST)*.

A **valid BST** is defined as follows:

	- The left subtree of a node contains only nodes with keys **strictly less than** the node's key.
	- The right subtree of a node contains only nodes with keys **strictly greater than** the node's key.
	- Both the left and right subtrees must also be binary search trees.

 

Example 1:

```
**Input:** root = [2,1,3]
**Output:** true
```

Example 2:

```
**Input:** root = [5,1,4,null,null,3,6]
**Output:** false
**Explanation:** The root node's value is 5 but its right child's value is 4.
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[1, 10^4]`.
	- `-2^31 <= Node.val <= 2^31 - 1`

#### 💡 Revision note

```text
Pattern: Recursive bounds validation
Key idea: Maintain valid range for each node; tighten bounds when descending left/right subtrees.
Complexity: O(n) time / O(h) space, where h is tree height
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isValidBST(TreeNode root) {
        return isValidate(root,Long.MIN_VALUE,Long.MAX_VALUE);
    }

    private boolean isValidate(TreeNode root,long min,long max){
        if(root == null){
            return true;
        }

        if(root.val<=min || root.val>=max){
            return false;
        }

        
        return isValidate(root.left,min,root.val) && 
        isValidate(root.right,root.val,max);
    }
}
```

</details>

### 🟡 230. Kth Smallest Element in a BST

**Medium** · 🏷️ Tree, Depth-First Search, Binary Search Tree, Binary Tree · 📅 2025-12-01

#### 📄 Problem

Given the `root` of a binary search tree, and an integer `k`, return *the* `k^th` *smallest value (**1-indexed**) of all the values of the nodes in the tree*.

 

Example 1:

```
**Input:** root = [3,1,4,null,2], k = 1
**Output:** 1
```

Example 2:

```
**Input:** root = [5,3,6,2,4,null,null,1], k = 3
**Output:** 3
```

 

**Constraints:**

	- The number of nodes in the tree is `n`.
	- `1 <= k <= n <= 10^4`
	- `0 <= Node.val <= 10^4`

 

**Follow up:** If the BST is modified often (i.e., we can do insert and delete operations) and you need to find the kth smallest frequently, how would you optimize?

#### 💡 Revision note

```text
Pattern: In-order traversal with min-heap
Key idea: In-order traversal of BST yields sorted values; heap enables extracting the kth smallest.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    PriorityQueue<Integer> q = new PriorityQueue<>((i,j)->i-j);
    public int kthSmallest(TreeNode root, int k) {
       addToQueue(root);

       while(k>1){
        q.poll();
        k--;
       }

    return q.peek();
        
    }

    private void addToQueue(TreeNode root){
        if(root == null){
            return;
        }
        addToQueue(root.left);
        if(root !=null){
            q.offer(root.val);
        }
        addToQueue(root.right);
    }
}
```

</details>

### 🟡 235. Lowest Common Ancestor of a Binary Search Tree

**Medium** · 🏷️ Tree, Depth-First Search, Binary Search Tree, Binary Tree · 📅 2025-10-29

#### 📄 Problem

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

 

Example 1:

```
**Input:** root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
**Output:** 6
**Explanation:** The LCA of nodes 2 and 8 is 6.
```

Example 2:

```
**Input:** root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
**Output:** 2
**Explanation:** The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

Example 3:

```
**Input:** root = [2,1], p = 2, q = 1
**Output:** 2
```

 

**Constraints:**

	- The number of nodes in the tree is in the range `[2, 10^5]`.
	- `-10^9 <= Node.val <= 10^9`
	- All `Node.val` are **unique**.
	- `p != q`
	- `p` and `q` will exist in the BST.

#### 💡 Revision note

```text
Pattern: Post-order DFS
Key idea: LCA is the first node where both search targets exist in separate subtrees or is one of them.
Complexity: O(n) time / O(h) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {

        if(root == null){
            return null;
        }
        if(root.val == p.val || root.val == q.val){
            return root;
        }

        TreeNode right = lowestCommonAncestor(root.right, p,q);
        TreeNode left = lowestCommonAncestor(root.left,p,q);

        if(right!=null && left!=null){
            return root;
        }
        if(right!=null){
            return right;
        }
        return left;
        
    }
}
```

</details>

---

## Bit Manipulation (3)

### 🟡 78. Subsets

**Medium** · 🏷️ Array, Backtracking, Bit Manipulation · 📅 2025-12-08

#### 📄 Problem

Given an integer array `nums` of **unique** elements, return *all possible* *subsets* *(the power set)*.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

 

Example 1:

```
**Input:** nums = [1,2,3]
**Output:** [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

Example 2:

```
**Input:** nums = [0]
**Output:** [[],[0]]
```

 

**Constraints:**

	- `1 <= nums.length <= 10`
	- `-10 <= nums[i] <= 10`
	- All the numbers of `nums` are **unique**.

#### 💡 Revision note

```text
Pattern: Recursive backtracking
Key idea: Each element's binary decision (include/exclude) at each level generates all 2^n possible subsets when explored exhaustively.
Complexity: O(n * 2^n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        int n = nums.length;
        List<Integer> list = new ArrayList<>();
        List<List<Integer>> res = new ArrayList<>();
        subsequence(nums,0,n,list,res);
        return res;
        
    }


    private void subsequence(int[] nums, int i, int n, List<Integer> list, List<List<Integer>> res){
        if( i==n ){
            res.add(list);
            return;
        }
        List<Integer> list2 = new ArrayList<>(list);
        list2.add(nums[i]);
        subsequence(nums, i+1, n , list2, res);
        subsequence(nums, i+1, n , list, res);        
    }
}
```

</details>

### 🟡 90. Subsets II

**Medium** · 🏷️ Array, Backtracking, Bit Manipulation · 📅 2025-12-11

#### 📄 Problem

Given an integer array `nums` that may contain duplicates, return *all possible* *subsets** (the power set)*.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

 

Example 1:

```
**Input:** nums = [1,2,2]
**Output:** [[],[1],[1,2],[1,2,2],[2],[2,2]]
```
Example 2:

```
**Input:** nums = [0]
**Output:** [[],[0]]
```

 

**Constraints:**

	- `1 <= nums.length <= 10`
	- `-10 <= nums[i] <= 10`

#### 💡 Revision note

```text
Pattern: Backtracking with duplicate skipping
Key idea: Sort to group duplicates, skip all when excluding an element to prevent duplicate subsets.
Complexity: O(n * 2^n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {

        Arrays.sort(nums);

        List<List<Integer>> res = new ArrayList<>();
        List<Integer>  curr = new ArrayList<>();

        subset2(nums,curr,res,0,nums.length);
        return res;
        
    }


    private void subset2(int[] arr , List<Integer> curr, List<List<Integer>> res , int i, int n){

        if(i == n ){
            res.add(new ArrayList<>(curr));
            //System.out.println(curr.size());
            return;
        }

        curr.add(arr[i]);
        //System.out.println(curr.size());
        subset2(arr,curr,res,i+1,n);

        curr.remove(curr.size()-1);
        //System.out.println(curr.size());
        int idx = i+1;
        while(idx<n && arr[idx]==arr[idx-1]){
            idx++;
        }
        subset2(arr,curr,res,idx,n);
    }
}
```

</details>

### 🟡 287. Find the Duplicate Number

**Medium** · 🏷️ Array, Two Pointers, Binary Search, Bit Manipulation · 📅 2025-11-16

#### 📄 Problem

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only **one repeated number** in `nums`, return *this repeated number*.

You must solve the problem **without** modifying the array `nums` and using only constant extra space.

 

Example 1:

```
**Input:** nums = [1,3,4,2,2]
**Output:** 2
```

Example 2:

```
**Input:** nums = [3,1,3,4,2]
**Output:** 3
```

Example 3:

```
**Input:** nums = [3,3,3,3,3]
**Output:** 3
```

 

**Constraints:**

	- `1 <= n <= 10^5`
	- `nums.length == n + 1`
	- `1 <= nums[i] <= n`
	- All the integers in `nums` appear only **once** except for **precisely one integer** which appears **two or more** times.

 

**Follow up:**

	- How can we prove that at least one duplicate number must exist in `nums`?
	- Can you solve the problem in linear runtime complexity?

#### 💡 Revision note

```text
Pattern: Floyd's Cycle Detection
Key idea: Array values form linked list; duplicate is the cycle entrance.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int findDuplicate(int[] nums) {

        Map<Integer,Integer> map = new HashMap<>();

        for(int i : nums){
            map.put(i,map.getOrDefault(i,0)+1);
        }
        
        for(int i =1;i<=nums.length ;i++){
            if(map.get(i)!=null){
                if(map.get(i)>1)
                    return i;
            }
        }
        return -1;
    }
}
```

</details>

---

## Divide and Conquer (3)

### 🟡 53. Maximum Subarray

**Medium** · 🏷️ Array, Divide and Conquer, Dynamic Programming · 📅 2025-12-16

#### 📄 Problem

Given an integer array `nums`, find the subarray with the largest sum, and return *its sum*.

 

Example 1:

```
**Input:** nums = [-2,1,-3,4,-1,2,1,-5,4]
**Output:** 6
**Explanation:** The subarray [4,-1,2,1] has the largest sum 6.
```

Example 2:

```
**Input:** nums = [1]
**Output:** 1
**Explanation:** The subarray [1] has the largest sum 1.
```

Example 3:

```
**Input:** nums = [5,4,-1,7,8]
**Output:** 23
**Explanation:** The subarray [5,4,-1,7,8] has the largest sum 23.
```

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `-10^4 <= nums[i] <= 10^4`

 

**Follow up:** If you have figured out the `O(n)` solution, try coding another solution using the **divide and conquer** approach, which is more subtle.

#### 💡 Revision note

```text
Pattern: Kadane's Algorithm
Key idea: At each position, decide to extend the subarray or start fresh, tracking the best sum.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int ans = nums[0];
        int curr = 0;

        for(int i=0; i<nums.length; i++){
            curr += nums[i];
            curr = Math.max(curr, nums[i]);
            ans  = Math.max(ans, curr);
        }

        return ans;
        
    }
}
```

</details>

### 🟡 105. Construct Binary Tree from Preorder and Inorder Traversal

**Medium** · 🏷️ Array, Hash Table, Divide and Conquer, Tree, Binary Tree · 📅 2025-11-25

#### 📄 Problem

Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return *the binary tree*.

 

Example 1:

```
**Input:** preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
**Output:** [3,9,20,null,null,15,7]
```

Example 2:

```
**Input:** preorder = [-1], inorder = [-1]
**Output:** [-1]
```

 

**Constraints:**

	- `1 <= preorder.length <= 3000`
	- `inorder.length == preorder.length`
	- `-3000 <= preorder[i], inorder[i] <= 3000`
	- `preorder` and `inorder` consist of **unique** values.
	- Each value of `inorder` also appears in `preorder`.
	- `preorder` is **guaranteed** to be the preorder traversal of the tree.
	- `inorder` is **guaranteed** to be the inorder traversal of the tree.

#### 💡 Revision note

```text
Pattern: Preorder + Inorder Reconstruction
Key idea: Preorder identifies root first; inorder position splits left and right subtrees; HashMap enables O(1) lookups.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int preorderindex =0;
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        int n = preorder.length;
        HashMap<Integer,Integer> inOrderMap = new HashMap<>();
        for(int i =0 ;i<n; i++){
            inOrderMap.put(inorder[i],i);
        }
        int[] preorderindex ={0};
    
    return construtTree(preorder,inorder,preorderindex,0,n-1,inOrderMap);

    }

    private TreeNode construtTree(int[] preorder, int[] inorder, 
                            int[] preorderindex, int left, int right,
                            HashMap<Integer,Integer> inOrderMap ){
        
        if(left>right){
            return null;
        }
        int rootVal = preorder[preorderindex[0]];
        preorderindex[0]++;
        TreeNode root = new TreeNode(rootVal);
        int inorderIndex = inOrderMap.get(rootVal);
        root.left = construtTree(preorder,inorder,preorderindex,left,inorderIndex-1,inOrderMap);
        root.right = construtTree(preorder,inorder,preorderindex,inorderIndex+1,right,inOrderMap);

        return root;
        
    }
}
```

</details>

### 🔴 4. Median of Two Sorted Arrays

**Hard** · 🏷️ Array, Binary Search, Divide and Conquer · 📅 2025-11-10

#### 📄 Problem

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.

 

Example 1:

```
**Input:** nums1 = [1,3], nums2 = [2]
**Output:** 2.00000
**Explanation:** merged array = [1,2,3] and median is 2.
```

Example 2:

```
**Input:** nums1 = [1,2], nums2 = [3,4]
**Output:** 2.50000
**Explanation:** merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

 

**Constraints:**

	- `nums1.length == m`
	- `nums2.length == n`
	- `0 <= m <= 1000`
	- `0 <= n <= 1000`
	- `1 <= m + n <= 2000`
	- `-10^6 <= nums1[i], nums2[i] <= 10^6`

#### 💡 Revision note

```text
Pattern: Two-pointer partial merge
Key idea: Track the last two values while advancing through both arrays to directly identify median elements without full merge.
Complexity: O(m+n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {

        int n = nums1.length;
        int m = nums2.length;

        int i = 0;
        int j = 0;

        int m1 = -1;
        int m2 = -1;

        for(int c = 0 ; c<=(n+m)/2; c++){
            m2 = m1;

            if(i!=n && j!=m){
                m1 = nums1[i]>nums2[j] ? nums2[j++]: nums1[i++];
            }
            else if(i<n){
                m1 = nums1[i++];
            }
            else{
                m1= nums2[j++];
            }
        }

        if((n+m)%2 == 0){
            return (m1+m2)/2.0;
        }else
            return m1;
    }
}
```

</details>

---

## Math (3)

### 🟡 150. Evaluate Reverse Polish Notation

**Medium** · 🏷️ Array, Math, Stack · 📅 2025-11-05

#### 📄 Problem

You are given an array of strings `tokens` that represents an arithmetic expression in a Reverse Polish Notation.

Evaluate the expression. Return *an integer that represents the value of the expression*.

**Note** that:

	- The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
	- Each operand may be an integer or another expression.
	- The division between two integers always **truncates toward zero**.
	- There will not be any division by zero.
	- The input represents a valid arithmetic expression in a reverse polish notation.
	- The answer and all the intermediate calculations can be represented in a **32-bit** integer.

 

Example 1:

```
**Input:** tokens = ["2","1","+","3","*"]
**Output:** 9
**Explanation:** ((2 + 1) * 3) = 9
```

Example 2:

```
**Input:** tokens = ["4","13","5","/","+"]
**Output:** 6
**Explanation:** (4 + (13 / 5)) = 6
```

Example 3:

```
**Input:** tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
**Output:** 22
**Explanation:** ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

 

**Constraints:**

	- `1 <= tokens.length <= 10^4`
	- `tokens[i]` is either an operator: `"+"`, `"-"`, `"*"`, or `"/"`, or an integer in the range `[-200, 200]`.

#### 💡 Revision note

```text
Pattern: Stack-based RPN evaluation
Key idea: Postfix notation processes operands before operators, so pushing values then popping operands when operators appear naturally evaluates the expression.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int evalRPN(String[] tokens) {
        int n = tokens.length;
        Stack<Integer> stack = new Stack<>();
        Set<String> operators = Set.of("+","-","*","/");
        for(int i = 0;i<n;i++){
            if(operators.contains(tokens[i])){
                int a = stack.pop();
                int b = stack.pop();
                int ans = perform(b,a,tokens[i]);
                stack.push(ans);
            }else{
                stack.push(Integer.valueOf(tokens[i]));
            }
        }
        return stack.peek();
    }

    private int perform(int a, int b , String o){
        int ans = 0;
        switch(o){
            case "+":
                ans = a+b;
                break;
            case "-":
                ans = a-b;
                break;
            case "*":
                ans = a*b;
                break;
            case "/":
                ans = a/b;
                break;
            default:
                break;
        }
        return ans;
    }
}
```

</details>

### 🟡 189. Rotate Array

**Medium** · 🏷️ Array, Math, Two Pointers · 📅 2025-01-06

#### 📄 Problem

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

 

Example 1:

```
**Input:** nums = [1,2,3,4,5,6,7], k = 3
**Output:** [5,6,7,1,2,3,4]
**Explanation:**
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

Example 2:

```
**Input:** nums = [-1,-100,3,99], k = 2
**Output:** [3,99,-1,-100]
**Explanation:** 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `-2^31 <= nums[i] <= 2^31 - 1`
	- `0 <= k <= 10^5`

 

**Follow up:**

	- Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
	- Could you do it in-place with `O(1)` extra space?

#### 💡 Revision note

```text
Reversal rotation
Reversing last k, then first n−k, then entire array rotates it in-place.
O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public void rotate(int[] nums, int k) {
        
        if( k > nums.length)
            k= k % nums.length;

        nums = reverse(nums,nums.length-1,nums.length-k);
        nums = reverse(nums,nums.length-1-k,0);
        nums = reverse(nums, nums.length-1,0);

        
    }

    private int[] reverse(int num[], int start, int end){
        while(start > end ){
            int temp = num[start];
            num[start] = num[end];
            num[end] = temp;
            start --;
            end ++;
        }
        return num;
    }
}

```

</details>

### 🟡 3021. Alice and Bob Playing Flower Game

**Medium** · 🏷️ Math · 📅 2025-08-29

#### 📄 Problem

Alice and Bob are playing a turn-based game on a field, with two lanes of flowers between them. There are `x` flowers in the first lane between Alice and Bob, and `y` flowers in the second lane between them.

The game proceeds as follows:

	- Alice takes the first turn.
	- In each turn, a player must choose either one of the lane and pick one flower from that side.
	- At the end of the turn, if there are no flowers left at all in either lane, the **current** player captures their opponent and wins the game.

Given two integers, `n` and `m`, the task is to compute the number of possible pairs `(x, y)` that satisfy the conditions:

	- Alice must win the game according to the described rules.
	- The number of flowers `x` in the first lane must be in the range `[1,n]`.
	- The number of flowers `y` in the second lane must be in the range `[1,m]`.

Return *the number of possible pairs* `(x, y)` *that satisfy the conditions mentioned in the statement*.

 

Example 1:

```
**Input:** n = 3, m = 2
**Output:** 3
**Explanation:** The following pairs satisfy conditions described in the statement: (1,2), (3,2), (2,1).
```

Example 2:

```
**Input:** n = 1, m = 1
**Output:** 0
**Explanation:** No pairs satisfy the conditions described in the statement.
```

 

**Constraints:**

	- `1 <= n, m <= 10^5`

#### 💡 Revision note

```text
Pattern: Parity analysis + combinatorial counting
Key idea: Alice wins when x+y is odd (she makes the final move); count pairs where x and y have different parity.
Complexity: O(1) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public long flowerGame(int n, int m) {
        return ((long)m*n)/2;
        // int x = 1; 
        // int y = 1;
        // int res = 0;

        // if((n+m) ==2 ){
        //     return 0;
        // }
        // else{
        //     for(int i = 1;i<=n;i++){
        //     for(int j = 1;j<=m;j++){
        //         if((i+j)%2 != 0){
        //             res++;
        //         }
        //     }
        // }
        // }
        

        
        // return res;
    }
}
```

</details>

---

## Array (2)

### 🟢 485. Max Consecutive Ones

**Easy** · 🏷️ Array · 📅 2026-07-13

#### 📄 Problem

Given a binary array `nums`, return *the maximum number of consecutive *`1`*'s in the array*.

 

Example 1:

```
**Input:** nums = [1,1,0,1,1,1]
**Output:** 3
**Explanation:** The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
```

Example 2:

```
**Input:** nums = [1,0,1,1,0,1]
**Output:** 2
```

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `nums[i]` is either `0` or `1`.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {

        int n = nums.length;
        int curr = 0;
        int ans = 0;
        for(int i=0; i<n; i++){
            if(nums[i]==0){
                ans = Integer.max(curr,ans);
                curr = 0;
            }else{
                curr++;
            }
        }
        ans = Integer.max(curr,ans);
        return ans;
        
    }
}
```

</details>

### 🟢 1299. Replace Elements with Greatest Element on Right Side

**Easy** · 🏷️ Array · 📅 2026-07-12

#### 📄 Problem

Given an array `arr`, replace every element in that array with the greatest element among the elements to its right, and replace the last element with `-1`.

After doing so, return the array.

 

Example 1:

```
**Input:** arr = [17,18,5,4,6,1]
**Output:** [18,6,6,6,1,-1]
**Explanation:** 
- index 0 --> the greatest element to the right of index 0 is index 1 (18).
- index 1 --> the greatest element to the right of index 1 is index 4 (6).
- index 2 --> the greatest element to the right of index 2 is index 4 (6).
- index 3 --> the greatest element to the right of index 3 is index 4 (6).
- index 4 --> the greatest element to the right of index 4 is index 5 (1).
- index 5 --> there are no elements to the right of index 5, so we put -1.
```

Example 2:

```
**Input:** arr = [400]
**Output:** [-1]
**Explanation:** There are no elements to the right of index 0.
```

 

**Constraints:**

	- `1 <= arr.length <= 10^4`
	- `1 <= arr[i] <= 10^5`

#### 💡 Revision note

```text
Pattern: Right-to-left single pass
Key idea: Traversing backwards, we store the maximum of all right elements at each position, updating max as we go.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int n = arr.length;

        int[] pf = new int[n];
        pf[n-1]=-1;
        int maxTillNow = Integer.max(pf[n-1],arr[n-1]);

        for(int i = n-2; i>=0; i--){
            pf[i]=maxTillNow;
            maxTillNow = Integer.max(pf[i],arr[i]);
        }

        return pf;
        
    }
}
```

</details>

---

## Breadth-First Search (2)

### 🟡 322. Coin Change

**Medium** · 🏷️ Array, Dynamic Programming, Breadth-First Search · 📅 2026-01-05

#### 📄 Problem

You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return *the fewest number of coins that you need to make up that amount*. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.

 

Example 1:

```
**Input:** coins = [1,2,5], amount = 11
**Output:** 3
**Explanation:** 11 = 5 + 5 + 1
```

Example 2:

```
**Input:** coins = [2], amount = 3
**Output:** -1
```

Example 3:

```
**Input:** coins = [1], amount = 0
**Output:** 0
```

 

**Constraints:**

	- `1 <= coins.length <= 12`
	- `1 <= coins[i] <= 2^31 - 1`
	- `0 <= amount <= 10^4`

#### 💡 Revision note

```text
Pattern: Unbounded knapsack DP
Key idea: For each coin, decide to use it (unlimited) or skip; memoize minimum coins needed.
Complexity: O(n × amount) time / O(n × amount) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int coinChange(int[] coins, int amount) {

        int n = coins.length;
        int[][] dp = new int[n][amount+1];
        for(int i = 0 ; i< n;i++){
            Arrays.fill(dp[i],-1);
        }
        int ans = findmin(n-1,coins,amount,dp);
        return ans == (int)1e9 ? -1 : ans;
        
    }

    private int findmin(int i, int[] arr, int t, int[][] dp){

        if(i == 0){
            return (t % arr[i]) == 0 ? t / arr[i] : (int)1e9;
        }
        
        if(dp[i][t]!=-1){
            return dp[i][t];
        }
        int pick =  (int)1e9;
        if(arr[i]<=t){
            pick =  1 + findmin(i, arr, t-arr[i],dp);
        }
        int nonpick =   findmin(i-1, arr, t,dp);

        return dp[i][t]=Integer.min(pick,nonpick);


    }
}
```

</details>

### 🟡 1306. Jump Game III

**Medium** · 🏷️ Array, Depth-First Search, Breadth-First Search · 📅 2026-06-20

#### 📄 Problem

Given an array of non-negative integers `arr`, you are initially positioned at `start` index of the array. When you are at index `i`, you can jump to `i + arr[i]` or `i - arr[i]`, check if you can reach **any** index with value 0.

Notice that you can not jump outside of the array at any time.

 

Example 1:

```
**Input:** arr = [4,2,3,0,3,1,2], start = 5
**Output:** true
**Explanation:** 
All possible ways to reach at index 3 with value 0 are: 
index 5 -> index 4 -> index 1 -> index 3 
index 5 -> index 6 -> index 4 -> index 1 -> index 3
```

Example 2:

```
**Input:** arr = [4,2,3,0,3,1,2], start = 0
**Output:** true 
**Explanation: 
**One possible way to reach at index 3 with value 0 is: 
index 0 -> index 4 -> index 1 -> index 3
```

Example 3:

```
**Input:** arr = [3,0,2,1,2], start = 2
**Output:** false
**Explanation: **There is no way to reach at index 1 with value 0.
```

 

**Constraints:**

	- `1 <= arr.length <= 5 * 10^4`
	- `0 <= arr[i] < arr.length`
	- `0 <= start < arr.length`

#### 💡 Revision note

```text
Pattern: DFS with memoization
Key idea: DFS explores all reachable indices; memoization prevents redundant computation and infinite loops.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean canReach(int[] arr, int start) {

        int n = arr.length;
        Boolean[] val = new Boolean[n];
        return canReach(arr,start,val,n);
        
    }

    private boolean canReach(int[] arr, int i, Boolean[] val,int n){

        if(i>=n || i<0){
            return false;
        }
        if(arr[i]==0){
            return true;
        }

        if(val[i]!=null){
            return val[i];
        }

        val[i] = false; 

        if(canReach(arr,i+arr[i],val,n)  || canReach(arr,i-arr[i],val,n)){
            return val[i] = true;
        }
        return val[i];

    }
}
```

</details>

---

## Prefix Sum (2)

### 🟡 238. Product of Array Except Self

**Medium** · 🏷️ Array, Prefix Sum · 📅 2025-11-01

#### 📄 Problem

Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

 

Example 1:

```
**Input:** nums = [1,2,3,4]
**Output:** [24,12,8,6]
```
Example 2:

```
**Input:** nums = [-1,1,0,-3,3]
**Output:** [0,0,9,0,0]
```

 

**Constraints:**

	- `2 <= nums.length <= 10^5`
	- `-30 <= nums[i] <= 30`
	- The input is generated such that `answer[i]` is **guaranteed** to fit in a **32-bit** integer.

 

**Follow up:** Can you solve the problem in `O(1)` extra space complexity? (The output array **does not** count as extra space for space complexity analysis.)

#### 💡 Revision note

```text
Pattern: Prefix and Suffix Products
Key idea: Product except nums[i] equals left product (before i) times right product (after i).
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] prefix = new int[n];
        int[] suffix = new int[n];
        prefix[0]=nums[0];
        suffix[n-1]=nums[n-1];
        for(int i = 1; i<nums.length; i++){
            prefix[i]=prefix[i-1]*nums[i];
        }
        for(int i = n-2;i>=0;i--){
            suffix[i]=suffix[i+1]*nums[i];
        }
        int[] ans = new int[n];
        for(int i = 0;i<n;i++){
            if(i==0){
                ans[i]=suffix[i+1];
            }else if(i==n-1){
                ans[i]=prefix[i-1];
            }else{
                ans[i]=prefix[i-1]*suffix[i+1];
            }
            
        }
        return ans;
    }
}
```

</details>

### 🟡 560. Subarray Sum Equals K

**Medium** · 🏷️ Array, Hash Table, Prefix Sum · 📅 2025-11-04

#### 📄 Problem

Given an array of integers `nums` and an integer `k`, return *the total number of subarrays whose sum equals to* `k`.

A subarray is a contiguous **non-empty** sequence of elements within an array.

 

Example 1:

```
**Input:** nums = [1,1,1], k = 2
**Output:** 2
```
Example 2:

```
**Input:** nums = [1,2,3], k = 3
**Output:** 2
```

 

**Constraints:**

	- `1 <= nums.length <= 2 * 10^4`
	- `-1000 <= nums[i] <= 1000`
	- `-10^7 <= k <= 10^7`

#### 💡 Revision note

```text
Pattern: Prefix sum + hashmap
Key idea: Track prefix sums in a map; when current_sum - k exists, count how many subarrays before this point sum to k.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int subarraySum(int[] arr, int tar) {
        int curr = 0;
        int ans = 0;
        int n = arr.length;
        Map<Integer,Integer> map = new HashMap<>();
        map.put(0,1);
        for(int i =0;i<n;i++){
            curr +=arr[i];
            if(map.containsKey(curr-tar)){
                ans+=map.get(curr-tar);
            }
            map.put(curr,map.getOrDefault(curr,0)+1);
        }
        return ans;
    }
}
```

</details>

---

## Stack (2)

### 🟢 20. Valid Parentheses

**Easy** · 🏷️ String, Stack · 📅 2026-02-28

#### 📄 Problem

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

	- Open brackets must be closed by the same type of brackets.
	- Open brackets must be closed in the correct order.
	- Every close bracket has a corresponding open bracket of the same type.

 

Example 1:

**Input:** s = "()"

**Output:** true

Example 2:

**Input:** s = "()[]{}"

**Output:** true

Example 3:

**Input:** s = "(]"

**Output:** false

Example 4:

**Input:** s = "([])"

**Output:** true

Example 5:

**Input:** s = "([)]"

**Output:** false

 

**Constraints:**

	- `1 <= s.length <= 10^4`
	- `s` consists of parentheses only `'()[]{}'`.

#### 💡 Revision note

```text
Pattern: Stack-based bracket matching
Key idea: Stack handles LIFO matching—closing brackets pair with the most recent unmatched opening bracket of same type.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean isValid(String str) {
        Stack<Character> s = new Stack<>();
        int n = str.length();
        int i = 0;
        Set<Character> s1 = Set.of('(','{','[');
        Map<Character,Character> m = Map.of('(',')','{','}','[',']');
        while(i<n){
            if(s1.contains(str.charAt(i))){
                s.push(str.charAt(i));
            }else{
                if(!s.isEmpty() && str.charAt(i) == m.get(s.peek())){
                    s.pop();
                }else{
                    return false;
                }
            }
            
            i++;
        }
        return s.isEmpty() ? true:false;
    }
}
```

</details>

### 🟡 678. Valid Parenthesis String

**Medium** · 🏷️ String, Dynamic Programming, Stack, Greedy · 📅 2026-07-05

#### 📄 Problem

Given a string `s` containing only three types of characters: `'('`, `')'` and `'*'`, return `true` *if* `s` *is **valid***.

The following rules define a **valid** string:

	- Any left parenthesis `'('` must have a corresponding right parenthesis `')'`.
	- Any right parenthesis `')'` must have a corresponding left parenthesis `'('`.
	- Left parenthesis `'('` must go before the corresponding right parenthesis `')'`.
	- `'*'` could be treated as a single right parenthesis `')'` or a single left parenthesis `'('` or an empty string `""`.

 

Example 1:

```
**Input:** s = "()"
**Output:** true
```
Example 2:

```
**Input:** s = "(*)"
**Output:** true
```
Example 3:

```
**Input:** s = "(*))"
**Output:** true
```

 

**Constraints:**

	- `1 <= s.length <= 100`
	- `s[i]` is `'('`, `')'` or `'*'`.

#### 💡 Revision note

```text
Pattern: Greedy range tracking
Key idea: Wildcards create flexible bracket states; track min/max unmatched opens to determine validity without exploring all possibilities.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean checkValidString(String s) {
        int lo = 0; // lowest possbile of (
        int hi = 0; // highest possbile of )

        for(char ch : s.toCharArray()){
            if(ch =='('){
                lo++;
                hi++;
            }
            else if(ch == ')'){
                lo--;
                hi--;
            }
            else{
                lo--;
                hi++;
            }

            lo = Integer.max(lo,0);
            if(hi<0){
                return false;
            }
        }

        return lo ==0;
       
        
    }


}
```

</details>

---

## Topological Sort (2)

### 🟡 207. Course Schedule

**Medium** · 🏷️ Depth-First Search, Breadth-First Search, Graph Theory, Topological Sort · 📅 2026-04-04

#### 📄 Problem

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [a_i, b_i]` indicates that you **must** take course `b_i` first if you want to take course `a_i`.

	- For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.

Return `true` if you can finish all courses. Otherwise, return `false`.

 

Example 1:

```
**Input:** numCourses = 2, prerequisites = [[1,0]]
**Output:** true
**Explanation:** There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.
```

Example 2:

```
**Input:** numCourses = 2, prerequisites = [[1,0],[0,1]]
**Output:** false
**Explanation:** There are a total of 2 courses to take. 
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
```

 

**Constraints:**

	- `1 <= numCourses <= 2000`
	- `0 <= prerequisites.length <= 5000`
	- `prerequisites[i].length == 2`
	- `0 <= a_i, b_i < numCourses`
	- All the pairs prerequisites[i] are **unique**.

#### 💡 Revision note

```text
Pattern: DFS cycle detection
Key idea: Back edges reveal cycles; detect them by finding nodes reachable in their own DFS path.
Complexity: O(V + E) time / O(V + E) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public boolean canFinish(int numCourses, int[][] arr) {

        int n = arr.length;
        List<List<Integer>> adj = new ArrayList<>();
        for(int i = 0; i<numCourses;i++){
            adj.add(new ArrayList<>());
        }

        for(int i = 0;i<n;i++){
            adj.get(arr[i][1]).add(arr[i][0]);
        }

        
        int[] vis = new int[numCourses];


        for(int i = 0;i<numCourses ;i++){
            if(vis[i]==0){
                if(!findtopo(i,vis,adj)){
                    return false;
                };
            }
        }

        return true;

        
    }


    private boolean findtopo(int i, int[] vis, List<List<Integer>> adj){



        if(vis[i] == 1){
            return false;
        };

        if(vis[i] == 2){
            return true;
        }

        vis[i]=1;

        for(int j : adj.get(i)){

                if(!findtopo(j,vis,adj)){
                    return false;
                };
        }
        vis[i]=2;
        return true;
        

    }
}
```

</details>

### 🟡 210. Course Schedule II

**Medium** · 🏷️ Depth-First Search, Breadth-First Search, Graph Theory, Topological Sort · 📅 2026-04-05

#### 📄 Problem

There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [a_i, b_i]` indicates that you **must** take course `b_i` first if you want to take course `a_i`.

	- For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.

Return *the ordering of courses you should take to finish all courses*. If there are many valid answers, return **any** of them. If it is impossible to finish all courses, return **an empty array**.

 

Example 1:

```
**Input:** numCourses = 2, prerequisites = [[1,0]]
**Output:** [0,1]
**Explanation:** There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].
```

Example 2:

```
**Input:** numCourses = 4, prerequisites = [[1,0],[2,0],[3,1],[3,2]]
**Output:** [0,2,1,3]
**Explanation:** There are a total of 4 courses to take. To take course 3 you should have finished both courses 1 and 2. Both courses 1 and 2 should be taken after you finished course 0.
So one correct course order is [0,1,2,3]. Another correct ordering is [0,2,1,3].
```

Example 3:

```
**Input:** numCourses = 1, prerequisites = []
**Output:** [0]
```

 

**Constraints:**

	- `1 <= numCourses <= 2000`
	- `0 <= prerequisites.length <= numCourses * (numCourses - 1)`
	- `prerequisites[i].length == 2`
	- `0 <= a_i, b_i < numCourses`
	- `a_i != b_i`
	- All the pairs `[a_i, b_i]` are **distinct**.

#### 💡 Revision note

```text
Pattern: Topological Sort (DFS)
Key idea: Post-order DFS detects cycles via back edges; stack reversal yields the topological ordering.
Complexity: O(V + E) time / O(V + E) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] findOrder(int numCourses, int[][] prerequisites) {

        List<List<Integer>> adj = new ArrayList<>();
        for(int i = 0; i<numCourses; i++){
            adj.add(new ArrayList<>());
        }
        int n = prerequisites.length;
        

        for(int i=0; i<n; i++){
            adj.get(prerequisites[i][1]).add(prerequisites[i][0]);
        }

        int[] vis = new int[numCourses];
        Stack<Integer> s = new Stack<>();
        boolean b = false;

        for(int i =0;i<numCourses;i++){
            if(vis[i]==0){
                if(!dfs(i,adj,s,vis)){
                    return new int[]{};
                };
            }
        }

        int[] res = new int[numCourses];
        

        int i = 0;

        while(!s.isEmpty()){
            res[i++]= s.pop();
        }

        return res;
        
    }

    private boolean dfs(int i, List<List<Integer>> adj, Stack<Integer> s,int[] vis){

        if(vis[i] == 1){
            return false;
        }

        if(vis[i] == 2){
            return true;
        }

        vis[i]=1;

        for(int j : adj.get(i)){
            if(!dfs(j,adj,s,vis)){
                return false;
            }
        }

        vis[i]=2;
        s.push(i);
        return true;
    }
}
```

</details>

---

## Bucket Sort (1)

### 🟡 347. Top K Frequent Elements

**Medium** · 🏷️ Array, Hash Table, Divide and Conquer, Sorting, Heap (Priority Queue), Bucket Sort, Counting, Quickselect · 📅 2025-10-31

#### 📄 Problem

Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

 

Example 1:

**Input:** nums = [1,1,1,2,2,3], k = 2

**Output:** [1,2]

Example 2:

**Input:** nums = [1], k = 1

**Output:** [1]

Example 3:

**Input:** nums = [1,2,1,2,1,2,3,1,3,2], k = 2

**Output:** [1,2]

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `-10^4 <= nums[i] <= 10^4`
	- `k` is in the range `[1, the number of unique elements in the array]`.
	- It is **guaranteed** that the answer is **unique**.

 

**Follow up:** Your algorithm's time complexity must be better than `O(n log n)`, where n is the array's size.

#### 💡 Revision note

```text
Pattern: Bucket sort
Key idea: Group elements by frequency in array indices, skip sorting by iterating backward from max frequency.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer,Integer> map = new HashMap<>();
        int max = 0;
        for(int i : nums){
            map.put(i,map.getOrDefault(i,0)+1);
            max = Integer.max(max,map.get(i));
        }
        
        List<Integer>[] list = new ArrayList[max+1];

        for(Map.Entry<Integer,Integer> m : map.entrySet()){
            int count = m.getValue();
            if(list[count]==null){
                list[count]= new ArrayList<>();
            }
            list[count].add(m.getKey());
        }


        int[] ans = new int[k];

        int index = 0;
        for(int i = max; i>0 && index<k; i-- ){
            if(list[i]!=null){
                for(int m : list[i]){
                    ans[index++]=m;
                    if(index==k)
                        break;
                }
            }
        }
        return ans;
    }
}
```

</details>

---

## Combinatorics (1)

### 🟡 62. Unique Paths

**Medium** · 🏷️ Math, Dynamic Programming, Combinatorics · 📅 2025-12-28

#### 📄 Problem

There is a robot on an `m x n` grid. The robot is initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

Given the two integers `m` and `n`, return *the number of possible unique paths that the robot can take to reach the bottom-right corner*.

The test cases are generated so that the answer will be less than or equal to `2 * 10^9`.

 

Example 1:

```
**Input:** m = 3, n = 7
**Output:** 28
```

Example 2:

```
**Input:** m = 3, n = 2
**Output:** 3
**Explanation:** From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

 

**Constraints:**

	- `1 <= m, n <= 100`

#### 💡 Revision note

```text
Pattern: Top-down DP with memo
Key idea: Each cell reachable from only two directions; path count is sum of paths from above and left.
Complexity: O(m*n) time / O(m*n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int uniquePaths(int m, int n) {

        int[][] dp = new int[m][n];
        for(int i = 0;i<m;i++){
            Arrays.fill(dp[i],-1);
        }
        return findpath(m-1,n-1,dp);
        
    }

    private int findpath(int i, int j, int[][] dp ){

        if(i == 0 && j == 0){
            return 1;
        }
        if(i<0 || j<0){
            return 0;
        }

        if(dp[i][j]!=-1){
            return dp[i][j];
        }

        int up = findpath(i-1,j,dp);
        int le = findpath(i,j-1,dp);
        return dp[i][j]=up+le;
    }
}
```

</details>

---

## Counting (1)

### 🟡 621. Task Scheduler

**Medium** · 🏷️ Array, Hash Table, Greedy, Sorting, Heap (Priority Queue), Counting · 📅 2026-03-31

#### 📄 Problem

You are given an array of CPU `tasks`, each labeled with a letter from A to Z, and a number `n`. Each CPU interval can be idle or allow the completion of one task. Tasks can be completed in any order, but there's a constraint: there has to be a gap of **at least** `n` intervals between two tasks with the same label.

Return the **minimum** number of CPU intervals required to complete all tasks.

 

Example 1:

**Input:** tasks = ["A","A","A","B","B","B"], n = 2

**Output:** 8

**Explanation:** A possible sequence is: A -> B -> idle -> A -> B -> idle -> A -> B.

After completing task A, you must wait two intervals before doing A again. The same applies to task B. In the 3^rd interval, neither A nor B can be done, so you idle. By the 4^th interval, you can do A again as 2 intervals have passed.

Example 2:

**Input:** tasks = ["A","C","A","B","D","B"], n = 1

**Output:** 6

**Explanation:** A possible sequence is: A -> B -> C -> D -> A -> B.

With a cooling interval of 1, you can repeat a task after just one other task.

Example 3:

**Input:** tasks = ["A","A","A", "B","B","B"], n = 3

**Output:** 10

**Explanation:** A possible sequence is: A -> B -> idle -> idle -> A -> B -> idle -> idle -> A -> B.

There are only two types of tasks, A and B, which need to be separated by 3 intervals. This leads to idling twice between repetitions of these tasks.

 

**Constraints:**

	- `1 <= tasks.length <= 10^4`
	- `tasks[i]` is an uppercase English letter.
	- `0 <= n <= 100`

#### 💡 Revision note

```text
Pattern: Most frequent task bottleneck
Key idea: Most frequent task determines schedule length; must space occurrences n+1 apart, filling gaps with lower-frequency tasks.
Complexity: O(n) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int leastInterval(char[] tasks, int n) {

        int[] charMap = new int[26];
        int maxFreq = Integer.MIN_VALUE;
        int sameMaxFreqCount = 0;
        for(int i=0; i<tasks.length; i++){
            charMap[tasks[i]-'A']++;
            maxFreq = Integer.max(charMap[tasks[i]-'A'],maxFreq);
        }

        for(int i =0;i<26;i++){
            if(charMap[i] == maxFreq){
                sameMaxFreqCount++;
            }
        }

        System.out.println(sameMaxFreqCount);
        System.out.println(maxFreq);


        return Integer.max(tasks.length,((maxFreq-1)*(n+1))+sameMaxFreqCount);

        
    }
}
```

</details>

---

## Data Stream (1)

### 🟢 703. Kth Largest Element in a Stream

**Easy** · 🏷️ Tree, Design, Binary Search Tree, Heap (Priority Queue), Binary Tree, Data Stream · 📅 2026-03-21

#### 📄 Problem

You are part of a university admissions office and need to keep track of the `kth` highest test score from applicants in real-time. This helps to determine cut-off marks for interviews and admissions dynamically as new applicants submit their scores.

You are tasked to implement a class which, for a given integer `k`, maintains a stream of test scores and continuously returns the `k`th highest test score **after** a new score has been submitted. More specifically, we are looking for the `k`th highest score in the sorted list of all scores.

Implement the `KthLargest` class:

	- `KthLargest(int k, int[] nums)` Initializes the object with the integer `k` and the stream of test scores `nums`.
	- `int add(int val)` Adds a new test score `val` to the stream and returns the element representing the `k^th` largest element in the pool of test scores so far.

 

Example 1:

**Input:**

["KthLargest", "add", "add", "add", "add", "add"]

[[3, [4, 5, 8, 2]], [3], [5], [10], [9], [4]]

**Output:** [null, 4, 5, 5, 8, 8]

**Explanation:**

KthLargest kthLargest = new KthLargest(3, [4, 5, 8, 2]);

kthLargest.add(3); // return 4

kthLargest.add(5); // return 5

kthLargest.add(10); // return 5

kthLargest.add(9); // return 8

kthLargest.add(4); // return 8

Example 2:

**Input:**

["KthLargest", "add", "add", "add", "add"]

[[4, [7, 7, 7, 7, 8, 3]], [2], [10], [9], [9]]

**Output:** [null, 7, 7, 7, 8]

**Explanation:**

KthLargest kthLargest = new KthLargest(4, [7, 7, 7, 7, 8, 3]);

kthLargest.add(2); // return 7

kthLargest.add(10); // return 7

kthLargest.add(9); // return 7

kthLargest.add(9); // return 8

 

**Constraints:**

	- `0 <= nums.length <= 10^4`
	- `1 <= k <= nums.length + 1`
	- `-10^4 <= nums[i] <= 10^4`
	- `-10^4 <= val <= 10^4`
	- At most `10^4` calls will be made to `add`.

#### 💡 Revision note

```text
Pattern: Min-heap of size k
Key idea: Keep exactly k largest elements; min-heap's root is the kth largest overall.
Complexity: O(log k) per add / O(k) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class KthLargest {

    PriorityQueue<Integer> q = new PriorityQueue<>();
    int k;

    public KthLargest(int k, int[] nums) {
        this.k = k;

        for(int i = 0; i<nums.length; i++){
           add(nums[i]);
        }
    
    }
    
    public int add(int val) {

        q.offer(val);

        if(q.size()>k){
            q.poll();
        }

        return q.peek();



    }

}

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest obj = new KthLargest(k, nums);
 * int param_1 = obj.add(val);
 */
```

</details>

---

## Doubly-Linked List (1)

### 🟡 146. LRU Cache

**Medium** · 🏷️ Hash Table, Linked List, Design, Doubly-Linked List · 📅 2025-11-18

#### 📄 Problem

Design a data structure that follows the constraints of a **Least Recently Used (LRU) cache**.

Implement the `LRUCache` class:

	- `LRUCache(int capacity)` Initialize the LRU cache with **positive** size `capacity`.
	- `int get(int key)` Return the value of the `key` if the key exists, otherwise return `-1`.
	- `void put(int key, int value)` Update the value of the `key` if the `key` exists. Otherwise, add the `key-value` pair to the cache. If the number of keys exceeds the `capacity` from this operation, **evict** the least recently used key.

The functions `get` and `put` must each run in `O(1)` average time complexity.

 

Example 1:

```
**Input**
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]
**Output**
[null, null, null, 1, null, -1, null, -1, 3, 4]

**Explanation**
LRUCache lRUCache = new LRUCache(2);
lRUCache.put(1, 1); // cache is {1=1}
lRUCache.put(2, 2); // cache is {1=1, 2=2}
lRUCache.get(1);    // return 1
lRUCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
lRUCache.get(2);    // returns -1 (not found)
lRUCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}
lRUCache.get(1);    // return -1 (not found)
lRUCache.get(3);    // return 3
lRUCache.get(4);    // return 4
```

 

**Constraints:**

	- `1 <= capacity <= 3000`
	- `0 <= key <= 10^4`
	- `0 <= value <= 10^5`
	- At most `2 * 10^5` calls will be made to `get` and `put`.

#### 💡 Revision note

```text
Pattern: HashMap + doubly linked list
Key idea: HashMap provides O(1) key lookups; doubly-linked list maintains access order, enabling O(1) eviction of least-used items.
Complexity: O(1) time / O(capacity) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class LRUCache {

    int capacity = 0;
    Map<Integer,Node> map= new HashMap<>();
    Node head;
    Node tail;
    int filled = 0;
    class Node {

        int val;
        int key;
        Node next;
        Node prev;

        Node(){

        }
        Node(int val,int key){
            this.val = val;
            this.key = key;
        }
    }

    public LRUCache(int capacity) {
        this.capacity = capacity;
        head = new Node(-1,-1);
        tail = new Node(-1,-1);
        head.next = tail;
        tail.prev = head;
    }
    
    public int get(int key) {

        if(map.containsKey(key)){
            Node node = map.get(key);
            int v = node.val;
            delete(node);
            add(node);
            return v;
        }else{
            return -1;
        }
        
    }
    
    public void put(int key, int value) {

        if(map.containsKey(key)){
            Node node = map.get(key);
            delete(node);
            Node newNode = new Node(value,key);
            add(newNode);
            map.put(key,newNode);
        }else{
            Node node = new Node(value,key);
            map.put(key,node);
            add(node);
            filled++;
            if(filled > capacity){
                Node nodeToDelete = tail.prev;
                delete(nodeToDelete);
                map.remove(nodeToDelete.key);
            }
        }
        
    }

    public void add(Node node){

        Node temp = head.next;
        head.next = node;
        node.prev = head;
        node.next = temp;
        temp.prev = node;
    }

    public void delete(Node node){
        Node next = node.next;
        Node prev = node.prev;
        prev.next = next;
        next.prev = prev;
    }




}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```

</details>

---

## Enumeration (1)

### 🟢 1863. Sum of All Subset XOR Totals

**Easy** · 🏷️ Array, Math, Backtracking, Bit Manipulation, Combinatorics, Enumeration · 📅 2025-08-31

#### 📄 Problem

The **XOR total** of an array is defined as the bitwise `XOR` of** all its elements**, or `0` if the array is** empty**.

	- For example, the **XOR total** of the array `[2,5,6]` is `2 XOR 5 XOR 6 = 1`.

Given an array `nums`, return *the **sum** of all **XOR totals** for every **subset** of *`nums`. 

**Note:** Subsets with the **same** elements should be counted **multiple** times.

An array `a` is a **subset** of an array `b` if `a` can be obtained from `b` by deleting some (possibly zero) elements of `b`.

 

Example 1:

```
**Input:** nums = [1,3]
**Output:** 6
**Explanation: **The 4 subsets of [1,3] are:
- The empty subset has an XOR total of 0.
- [1] has an XOR total of 1.
- [3] has an XOR total of 3.
- [1,3] has an XOR total of 1 XOR 3 = 2.
0 + 1 + 3 + 2 = 6
```

Example 2:

```
**Input:** nums = [5,1,6]
**Output:** 28
**Explanation: **The 8 subsets of [5,1,6] are:
- The empty subset has an XOR total of 0.
- [5] has an XOR total of 5.
- [1] has an XOR total of 1.
- [6] has an XOR total of 6.
- [5,1] has an XOR total of 5 XOR 1 = 4.
- [5,6] has an XOR total of 5 XOR 6 = 3.
- [1,6] has an XOR total of 1 XOR 6 = 7.
- [5,1,6] has an XOR total of 5 XOR 1 XOR 6 = 2.
0 + 5 + 1 + 6 + 4 + 3 + 7 + 2 = 28
```

Example 3:

```
**Input:** nums = [3,4,5,6,7,8]
**Output:** 480
**Explanation:** The sum of all XOR totals for every subset is 480.
```

 

**Constraints:**

	- `1 <= nums.length <= 12`
	- `1 <= nums[i] <= 20`

#### 💡 Revision note

```text
Pattern: Recursive Backtracking
Key idea: Recursively enumerate all 2^n subsets (via include/exclude branching). Each contributes its XOR to the sum.
Complexity: O(2^n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int subsetXORSum(int[] nums) {
        return xor(nums , 0 ,0);
        
    }
    private int xor(int[] nums, int i, int currentXor){
        if(nums.length == i){
            return currentXor;
        }
        return xor(nums , i+1, (currentXor ^ nums[i])) + xor(nums , i+1, (currentXor ));
    }
}
```

</details>

---

## Geometry (1)

### 🟡 973. K Closest Points to Origin

**Medium** · 🏷️ Array, Math, Divide and Conquer, Geometry, Sorting, Heap (Priority Queue), Quickselect · 📅 2025-12-03

#### 📄 Problem

Given an array of `points` where `points[i] = [x_i, y_i]` represents a point on the **X-Y** plane and an integer `k`, return the `k` closest points to the origin `(0, 0)`.

The distance between two points on the **X-Y** plane is the Euclidean distance (i.e., `√(x_1 - x_2)^2 + (y_1 - y_2)^2`).

You may return the answer in **any order**. The answer is **guaranteed** to be **unique** (except for the order that it is in).

 

Example 1:

```
**Input:** points = [[1,3],[-2,2]], k = 1
**Output:** [[-2,2]]
**Explanation:**
The distance between (1, 3) and the origin is sqrt(10).
The distance between (-2, 2) and the origin is sqrt(8).
Since sqrt(8) < sqrt(10), (-2, 2) is closer to the origin.
We only want the closest k = 1 points from the origin, so the answer is just [[-2,2]].
```

Example 2:

```
**Input:** points = [[3,3],[5,-1],[-2,4]], k = 2
**Output:** [[3,3],[-2,4]]
**Explanation:** The answer [[-2,4],[3,3]] would also be accepted.
```

 

**Constraints:**

	- `1 <= k <= points.length <= 10^4`
	- `-10^4 <= x_i, y_i <= 10^4`

#### 💡 Revision note

```text
Pattern: Min Heap
Key idea: A min heap orders points by distance, enabling extraction of k smallest distances in O(k log n) time.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[][] kClosest(int[][] points, int k) {

    PriorityQueue<ArrayList<Integer>> q = new PriorityQueue<>((i,j)->i.get(2)-j.get(2));  

        int n = points.length;
        for(int i =0; i<n; i++){
            int[] arr = points[i];
            int x =arr[0];
            int y = arr[1];
            int ans = (x*x)+(y*y);
            ArrayList<Integer> list = new ArrayList<>();
            list.add(x);
            list.add(y);
            list.add(ans);
            q.offer(list);
        }

        int[][] res = new int[k][2];
        for(int i=0; i<k; i++){
            ArrayList<Integer> list = q.poll();
            res[i] = new int[]{list.get(0),list.get(1)};
        }
        return res;
        
    }
}
```

</details>

---

## Graph Theory (1)

### 🟡 133. Clone Graph

**Medium** · 🏷️ Hash Table, Depth-First Search, Breadth-First Search, Graph Theory · 📅 2026-04-01

#### 📄 Problem

Given a reference of a node in a **connected** undirected graph.

Return a **deep copy** (clone) of the graph.

Each node in the graph contains a value (`int`) and a list (`List[Node]`) of its neighbors.

```
class Node {
    public int val;
    public List<Node> neighbors;
}
```

 

**Test case format:**

For simplicity, each node's value is the same as the node's index (1-indexed). For example, the first node with `val == 1`, the second node with `val == 2`, and so on. The graph is represented in the test case using an adjacency list.

**An adjacency list** is a collection of unordered **lists** used to represent a finite graph. Each list describes the set of neighbors of a node in the graph.

The given node will always be the first node with `val = 1`. You must return the **copy of the given node** as a reference to the cloned graph.

 

Example 1:

```
**Input:** adjList = [[2,4],[1,3],[2,4],[1,3]]
**Output:** [[2,4],[1,3],[2,4],[1,3]]
**Explanation:** There are 4 nodes in the graph.
1st node (val = 1)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
2nd node (val = 2)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
3rd node (val = 3)'s neighbors are 2nd node (val = 2) and 4th node (val = 4).
4th node (val = 4)'s neighbors are 1st node (val = 1) and 3rd node (val = 3).
```

Example 2:

```
**Input:** adjList = [[]]
**Output:** [[]]
**Explanation:** Note that the input contains one empty list. The graph consists of only one node with val = 1 and it does not have any neighbors.
```

Example 3:

```
**Input:** adjList = []
**Output:** []
**Explanation:** This an empty graph, it does not have any nodes.
```

 

**Constraints:**

	- The number of nodes in the graph is in the range `[0, 100]`.
	- `1 <= Node.val <= 100`
	- `Node.val` is unique for each node.
	- There are no repeated edges and no self-loops in the graph.
	- The Graph is connected and all nodes can be visited starting from the given node.

#### 💡 Revision note

```text
Pattern: DFS with memoization
Key idea: Memoizing cloned nodes prevents infinite loops in cycles while maintaining original node-to-clone mappings.
Complexity: O(N + E) time / O(N) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {
    Map<Node, Node> map = new HashMap<>();

    public Node cloneGraph(Node node) {

        if(node==null){
            return null;
        }

        return generateClone(node);
        
    }

    private Node generateClone( Node node){

        // if(node == null){
        //     return null;
        // }

        if(!map.containsKey(node)){
            Node newNode = new Node(node.val);

            map.put(node,newNode);
            for(Node adj : node.neighbors){
                newNode.neighbors.add(generateClone(adj));
            }
        }

        return map.get(node);

    }
}
```

</details>

---

## Hash Function (1)

### 🟢 572. Subtree of Another Tree

**Easy** · 🏷️ Tree, Depth-First Search, String Matching, Binary Tree, Hash Function · 📅 2026-03-04

#### 📄 Problem

Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of` subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

 

Example 1:

```
**Input:** root = [3,4,5,1,2], subRoot = [4,1,2]
**Output:** true
```

Example 2:

```
**Input:** root = [3,4,5,1,2,null,null,null,null,0], subRoot = [4,1,2]
**Output:** false
```

 

**Constraints:**

	- The number of nodes in the `root` tree is in the range `[1, 2000]`.
	- The number of nodes in the `subRoot` tree is in the range `[1, 1000]`.
	- `-10^4 <= root.val <= 10^4`
	- `-10^4 <= subRoot.val <= 10^4`

#### 💡 Revision note

```text
Pattern: Tree DFS with identity check
Key idea: Traverse root tree to find a node whose subtree perfectly matches subRoot's structure and values.
Complexity: O(m*n) time / O(min(m,n)) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {

        if(root == null || subRoot == null){
            return false;
        }
        if(root.val == subRoot.val && isIdentical(root,subRoot)){
            return true;
        }
        return isSubtree(root.left,subRoot) || isSubtree(root.right,subRoot);
    }

    private boolean isIdentical(TreeNode root, TreeNode subtree){
        if(subtree == null && root == null){
            return true;
        }
        if(subtree == null || root == null){
            return false;
        }

        return root.val==subtree.val && 
        isIdentical(root.left,subtree.left) && 
        isIdentical(root.right,subtree.right);
    }
}
```

</details>

---

## Hash Table (1)

### 🟢 1. Two Sum

**Easy** · 🏷️ Array, Hash Table · 📅 2025-11-01

#### 📄 Problem

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

 

Example 1:

```
**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].
```

Example 2:

```
**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]
```

Example 3:

```
**Input:** nums = [3,3], target = 6
**Output:** [0,1]
```

 

**Constraints:**

	- `2 <= nums.length <= 10^4`
	- `-10^9 <= nums[i] <= 10^9`
	- `-10^9 <= target <= 10^9`
	- **Only one valid answer exists.**

 

**Follow-up: **Can you come up with an algorithm that is less than `O(n^2)` time complexity?

#### 💡 Revision note

```text
Pattern: Brute force
Key idea: Check all pairs until finding the sum that equals target.
Complexity: O(n²) time / O(1) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;

        for(int i = 0;i<n ;i++){
            for(int j = i+1;j<n;j++){
                if(nums[i]+nums[j]==target){
                    return new int[]{i,j};
                }
            }
        }
        return new int[]{-1};
    }
}
```

</details>

---

## Heap (Priority Queue) (1)

### 🟢 1046. Last Stone Weight

**Easy** · 🏷️ Array, Heap (Priority Queue) · 📅 2026-03-22

#### 📄 Problem

You are given an array of integers `stones` where `stones[i]` is the weight of the `i^th` stone.

We are playing a game with the stones. On each turn, we choose the **heaviest two stones** and smash them together. Suppose the heaviest two stones have weights `x` and `y` with `x <= y`. The result of this smash is:

	- If `x == y`, both stones are destroyed, and
	- If `x != y`, the stone of weight `x` is destroyed, and the stone of weight `y` has new weight `y - x`.

At the end of the game, there is **at most one** stone left.

Return *the weight of the last remaining stone*. If there are no stones left, return `0`.

 

Example 1:

```
**Input:** stones = [2,7,4,1,8,1]
**Output:** 1
**Explanation:** 
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of the last stone.
```

Example 2:

```
**Input:** stones = [1]
**Output:** 1
```

 

**Constraints:**

	- `1 <= stones.length <= 30`
	- `1 <= stones[i] <= 1000`

#### 💡 Revision note

```text
Pattern: Max-heap
Key idea: Max-heap efficiently extracts the two heaviest stones each iteration without repeatedly scanning the array.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int lastStoneWeight(int[] stones) {

        PriorityQueue<Integer> q = new PriorityQueue<>((i,j)->j-i);

        for(Integer stone: stones){
            q.offer(stone);
        }
        System.out.println(q.peek());
        if(q.size()==1){
            return q.peek();
        }

        while(q.size()>1){
            int a = q.poll();
            int b = q.poll();
            int val = Math.abs(a-b);
            if(val!=0){
                q.offer(val);
            }
        }
        return q.size()==0?0:q.peek();
        
    }
}
```

</details>

---

## Merge Sort (1)

### 🔴 23. Merge k Sorted Lists

**Hard** · 🏷️ Linked List, Divide and Conquer, Heap (Priority Queue), Merge Sort · 📅 2026-02-28

#### 📄 Problem

You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

*Merge all the linked-lists into one sorted linked-list and return it.*

 

Example 1:

```
**Input:** lists = [[1,4,5],[1,3,4],[2,6]]
**Output:** [1,1,2,3,4,4,5,6]
**Explanation:** The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted linked list:
1->1->2->3->4->4->5->6
```

Example 2:

```
**Input:** lists = []
**Output:** []
```

Example 3:

```
**Input:** lists = [[]]
**Output:** []
```

 

**Constraints:**

	- `k == lists.length`
	- `0 <= k <= 10^4`
	- `0 <= lists[i].length <= 500`
	- `-10^4 <= lists[i][j] <= 10^4`
	- `lists[i]` is sorted in **ascending order**.
	- The sum of `lists[i].length` will not exceed `10^4`.

#### 💡 Revision note

```text
Pattern: Heap-based merge
Key idea: Min-heap efficiently provides the smallest element for each merge step without comparing k lists repeatedly.
Complexity: O(N log N) time / O(N) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        PriorityQueue<Integer> q = new PriorityQueue<>((i,j)->i-j);
        ListNode head = new ListNode();
        for(ListNode node : lists){
            while(node != null){
                q.offer(node.val);
                node = node.next;
            }
        }

        ListNode node = new ListNode();
        ListNode res = node;

        while(!q.isEmpty()){
            ListNode temp = new ListNode(q.poll());
            node.next = temp;
            node = node.next;
        }

        return res.next;

    }
}
```

</details>

---

## Number Theory (1)

### 🟡 1492. The kth Factor of n

**Medium** · 🏷️ Math, Number Theory · 📅 2024-04-13

#### 📄 Problem

You are given two positive integers `n` and `k`. A factor of an integer `n` is defined as an integer `i` where `n % i == 0`.

Consider a list of all factors of `n` sorted in **ascending order**, return *the *`k^th`* factor* in this list or return `-1` if `n` has less than `k` factors.

 

Example 1:

```
**Input:** n = 12, k = 3
**Output:** 3
**Explanation:** Factors list is [1, 2, 3, 4, 6, 12], the 3^rd factor is 3.
```

Example 2:

```
**Input:** n = 7, k = 2
**Output:** 7
**Explanation:** Factors list is [1, 7], the 2^nd factor is 7.
```

Example 3:

```
**Input:** n = 4, k = 4
**Output:** -1
**Explanation:** Factors list is [1, 2, 4], there is only 3 factors. We should return -1.
```

 

**Constraints:**

	- `1 <= k <= n <= 1000`

 

**Follow up:**

Could you solve this problem in less than O(n) complexity?

#### 💡 Revision note

```text
Pattern: Trial division
Key idea: Check each integer from 1 to n for divisibility; ascending order ensures divisors are sorted for direct kth access.
Complexity: O(n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
    import java.util.*;
class Solution {
    public int kthFactor(int n, int k) {
        List<Integer> arr1 = new ArrayList<Integer>();
        int[] a = new int[1000];
        for(int i=1;i<=n;i++){
            if(n%i==0)
            {
               arr1.add(i);
            }
        }
        System.out.println(arr1.size());
        if(arr1.size() >= k){
            return arr1.get(k-1);
        }
        return -1;
    }
}
```

</details>

---

## Queue (1)

### 🔴 239. Sliding Window Maximum

**Hard** · 🏷️ Array, Queue, Sliding Window, Heap (Priority Queue), Monotonic Queue · 📅 2025-11-14

#### 📄 Problem

You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return *the max sliding window*.

 

Example 1:

```
**Input:** nums = [1,3,-1,-3,5,3,6,7], k = 3
**Output:** [3,3,5,5,6,7]
**Explanation:** 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       **3**
 1 [3  -1  -3] 5  3  6  7       **3**
 1  3 [-1  -3  5] 3  6  7      ** 5**
 1  3  -1 [-3  5  3] 6  7       **5**
 1  3  -1  -3 [5  3  6] 7       **6**
 1  3  -1  -3  5 [3  6  7]      **7**
```

Example 2:

```
**Input:** nums = [1], k = 1
**Output:** [1]
```

 

**Constraints:**

	- `1 <= nums.length <= 10^5`
	- `-10^4 <= nums[i] <= 10^4`
	- `1 <= k <= nums.length`

#### 💡 Revision note

```text
Pattern: Max heap with lazy deletion
Key idea: Heap naturally provides max; lazily remove outdated indices only when they surface at top.
Complexity: O(n log k) time / O(k) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        PriorityQueue<int[]> q = new PriorityQueue<>((i,j)->j[0]-i[0]);
        int n = nums.length;
        int[] res = new int[n-k+1];
        for(int i =0;i<k;i++){
            q.offer(new int[]{nums[i],i});
        }

        res[0] = q.peek()[0];

        for(int i = k; i<n ;i++){
            q.offer(new int[]{nums[i],i});
            while(!q.isEmpty() && q.peek()[1]<=i-k){
                q.poll();
            }
            res[i-k+1]=q.peek()[0];
        }
        return res;


    }
}
```

</details>

---

## Quickselect (1)

### 🟡 215. Kth Largest Element in an Array

**Medium** · 🏷️ Array, Divide and Conquer, Sorting, Heap (Priority Queue), Quickselect · 📅 2026-03-15

#### 📄 Problem

Given an integer array `nums` and an integer `k`, return *the* `k^th` *largest element in the array*.

Note that it is the `k^th` largest element in the sorted order, not the `k^th` distinct element.

Can you solve it without sorting?

 

Example 1:

```
**Input:** nums = [3,2,1,5,6,4], k = 2
**Output:** 5
```
Example 2:

```
**Input:** nums = [3,2,3,1,2,4,5,5,6], k = 4
**Output:** 4
```

 

**Constraints:**

	- `1 <= k <= nums.length <= 10^5`
	- `-10^4 <= nums[i] <= 10^4`

#### 💡 Revision note

```text
Pattern: Max Heap
Key idea: A max-heap keeps the largest element at top; remove k-1 largest elements to expose the kth largest.
Complexity: O(n log n) time / O(n) space
```

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        

        PriorityQueue<Integer> q = new PriorityQueue<Integer>((i,j)->j-i);
        int n = nums.length;
        for(int i = 0;i<n;i++){
            q.offer(nums[i]);
        }
        while(k>1){
            q.poll();
            k--;
        }
        return q.peek();
    }
}
```

</details>

---

## Simulation (1)

### 🟢 1929. Concatenation of Array

**Easy** · 🏷️ Array, Simulation · 📅 2026-07-12

#### 📄 Problem

Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` (**0-indexed**).

Specifically, `ans` is the **concatenation** of two `nums` arrays.

Return *the array *`ans`.

 

Example 1:

```
**Input:** nums = [1,2,1]
**Output:** [1,2,1,1,2,1]
**Explanation:** The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

Example 2:

```
**Input:** nums = [1,3,2,1]
**Output:** [1,3,2,1,1,3,2,1]
**Explanation:** The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[3],nums[0],nums[1],nums[2],nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

 

**Constraints:**

	- `n == nums.length`
	- `1 <= n <= 1000`
	- `1 <= nums[i] <= 1000`

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int n = nums.length;
        int[] ans = new int[2*n];

        for(int i=0;i<n;i++){
            ans[i]=nums[i];
            ans[i+n]=nums[i];
        }

        return ans;
    }
}
```

</details>

---

## String Matching (1)

### 🟢 1408. String Matching in an Array

**Easy** · 🏷️ Array, String, String Matching · 📅 2026-07-17

#### 📄 Problem

Given an array of string `words`, return all strings in* *`words`* *that are a substring of another word. You can return the answer in **any order**.

 

Example 1:

```
**Input:** words = ["mass","as","hero","superhero"]
**Output:** ["as","hero"]
**Explanation:** "as" is substring of "mass" and "hero" is substring of "superhero".
["hero","as"] is also a valid answer.
```

Example 2:

```
**Input:** words = ["leetcode","et","code"]
**Output:** ["et","code"]
**Explanation:** "et", "code" are substring of "leetcode".
```

Example 3:

```
**Input:** words = ["blue","green","bu"]
**Output:** []
**Explanation:** No string of words is substring of another string.
```

 

**Constraints:**

	- `1 <= words.length <= 100`
	- `1 <= words[i].length <= 30`
	- `words[i]` contains only lowercase English letters.
	- All the strings of `words` are **unique**.

#### 💡 Revision note

_(not generated yet — run `python3 sync.py` to fill this in)_

<details><summary><b>🧩 Solution (Java) — click to expand</b></summary>

```java
class Solution {
    public List<String> stringMatching(String[] words) {

        Set<String> set = new HashSet<>();
        for(int i = 0; i<words.length; i++){
            for(int j = 0; j<words.length ; j++){
                if (j == i) continue;
                if(words[i].contains(words[j])){
                    set.add(words[j]);
                }
            }
        }

        if("superhero".contains("hero")){
            System.out.println(true);
        }

        return new ArrayList<>(set);
        
    }
}
```

</details>

---

