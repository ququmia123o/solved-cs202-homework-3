Download Link: https://assignmentchef.com/product/solved-cs202-homework-3
<br>
<h1>Part 1</h1>

<ul>

 <li>[<em>5 points</em>] Insert the values 13<em>,</em>9<em>,</em>10<em>,</em>21<em>,</em>11<em>,</em>16<em>,</em>4<em>,</em>12<em>,</em>6 into an initially empty AVL tree in order. Show only the final tree after all insertions. Then, delete 10<em>,</em>9<em>,</em>6 in given order. Show only the final tree after all deletion operations.</li>

 <li>[<em>5 points</em>] Insert 15<em>,</em>13<em>,</em>9<em>,</em>5<em>,</em>12<em>,</em>8<em>,</em>7<em>,</em>4<em>,</em>0<em>,</em>6<em>,</em>2<em>,</em>1<em>,</em>3 into an empty min-heap. Show only the final heap as a tree (not as an array) after all insertions.</li>

 <li>[<em>15 points</em>] Let T<sub>1 </sub>and T<sub>2 </sub>be AVL trees such that the largest key in T<sub>1 </sub>is less than the smallest key in T<sub>2</sub>. Give an algorithm (in psuedocode) for procedure JOIN-AVLTREES(T<sub>1</sub>, T<sub>2</sub>) that joins these two AVL trees. The runtime should be O(log<em>n</em>), where <em>n </em>is the size of the resulting AVL tree. Justify in a few of sentences the correctness and efficiency of your algorithm.</li>

</ul>

<h1>Part 2 – Running Median</h1>

Use the given file names and function signatures during implementation. Feel free to write helper functions to accomplish certain tasks but remember to give meaningful function names.

<ul>

 <li>[<em>7,5 points</em>] Implement an array-based max-heap data structure named as MaxHeap for maintaining a list of integer values that supports the following operations:</li>

</ul>

Listing 2: MaxHeap

void insert(int value); // inserts integer into heap int peek(); // returns the value of the max element int extractMax(); // retrieves and removes the max element int size(); // returns the number of elements in the heap

Put your code into MaxHeap.h and MaxHeap.cpp files.

<ul>

 <li>[<em>7,5 points</em>] Implement an array-based min-heap data structure named as MinHeap for maintaining a list of integer values that supports the following operations:</li>

</ul>

Listing 3: MinHeap

void insert(int value); // inserts integer into heap int peek(); // returns the value of the min element int extractMin(); // retrieves and removes the min element int size(); // returns the number of elements in the heap

Put your code into MinHeap.h and MinHeap.cpp files.

<ul>

 <li>[<em>20 points</em>] Design a MedianHeap data structure reusing MaxHeap and MinHeap, which supports getting median of the elements in O(1) time and inserting an element in O(log<em>n</em>) If the length of the list is even, choose the larger value of the two middle elements as the median.</li>

</ul>

Listing 4: MedianHeap

void insert(int value); //inserts an element into MedianHeap int findMedian(); //returns the value of the median

Put your code into MedianHeap.h and MedianHeap.cpp files.

<h1>Part 3 – Huffman Coding</h1>

Huffman coding, in essence, is a lossless data compression algorithm. Consider the data which is a sequence of characters encoded in ASCII. In ASCII, every character is encoded with the same number of bits: 8 bits per character. The common characters, e.g., alphanumeric characters, punctuation, control characters, etc., use only 7 bits; there are 128 different characters that can be encoded with 7 bits. Huffman coding on the other hand, compresses data by using fewer bits to encode more frequently occurring characters so that not all characters are encoded with 8 bits.

Suppose that we have a 100,000 character data file that we wish to store. We observe that the characters in the file occur with the frequencies given by Table 1. That is, only 6 different characters appear, and the character ’a’ occurs 45,000 times. If we store it without compression we would need 700,000 bits. However with Huffman coding, we can compress the file to (45 · 1 + 13 · 3 + 12 · 3 + 16 · 3 + 9 · 4 + 5 · 4)·1,000 = 224,000 bits.

Table 1: A character-coding

a               b                c                d               e                f

Frequency (in thousands)             45             13              12              16              9                5

ASCII                                         1100001   1100010   1100011   1100100   1100101     1100110

Variable-length codeword             0             101            100            111          1101         1100

The main goal is to create a tree that corresponds to coding schemes that will be used to encode/decode a file. Huffman trees are a type of binary tree used in performing this kind of conversion. A Huffman tree includes all the characters of your data on the leaf nodes, with most frequent characters being closer to the root. The distance and path away from the root is used to determine what bits (what 0s and 1s) are used to represent each character. The Huffman tree of Table 1 is as follows.

In the pseudocode that follows, we assume that <em>C </em>is a set of <em>n </em>characters and that each character <em>c </em>in <em>C </em>is an object with an attribute <em>c.freq </em>giving its frequency. The algorithm uses a min-priority queue <em>Q</em>, keyed on the <em>freq </em>attribute, to identify the two least-frequent objects to merge together.

Algorithm 1: HUFFMAN(C)

<ul>

 <li>n = |C|;</li>

 <li>Q = C;</li>

 <li>for <em>i = 1 to n – 1 </em>do</li>

</ul>

4allocate a new node <em>z</em>;

5<em>z.left </em>= x = <em>EXTRACT</em>_<em>MIN</em>(<em>Q</em>);

6<em>z.right </em>= y = <em>EXTRACT</em>_<em>MIN</em>(<em>Q</em>);

7<em>z.freq </em>= <em>x.freq </em>+ <em>y.freq</em>;

8<em>INSERT</em>(<em>Q,z</em>);

<ul>

 <li>end</li>

 <li>return <em>EXTRACT_</em><em>MIN</em>(<em>Q</em>)</li>

</ul>

The steps of creating the Huffman tree of Table I is given in the next page as an example [1]. Your first objective should be to implement the min-heap data structure as an array of pointers in which each pointer points to a MinHeapNode.

Listing 5: MinHeapNode

struct MinHeapNode

{

char character; // An input character int freq; // Frequency of the character

MinHeapNode *left, *right; // Left and right child

};

Put your min-heap code into HuffmanHeap.h and HuffmanHeap.cpp files. After you are finished, transform your heap into a min-priority queue implementing Huffman coding and put the codes into HuffmanQueue.h and HuffmanQueue.cpp files. Design the Huffman coding algorithm and put your code into HuffmanCode.h and HuffmanCode.cpp files.

Add a main function to the main.cpp file which reads an input file of characters and their frequencies (i.e., e 9), and writes their coding schemes (i.e., e 1101) on an output file. Take input and output file names as arguments. At the end, write a basic makefile which compiles all your code and creates an executable file named hw3.

<h1>References</h1>

[1] T.M. Cormen, C. E. Leiserson, R. L. Rivest &amp; C. Stein. <em>Introduction to Algorithms</em>,

3rd edition. The MIT Press. 2001. 432