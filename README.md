# Java Collections Framework Cheat Sheet
This is a small cheat sheet and rules of thumb for using Java Collections Framework.
Sources:
* https://www.caveofprogramming.com/java-collections-framework/
* https://dzone.com/articles/linked-list-journey-continues
All the Java Collections Framework classes implement the ```Collection``` interface.
## Lists
Lists implement the ```List``` interface:
* ```ArrayList```
* ```Vector```
* ```LinkedList``` (this one implements the ```Queue``` and ```Deque``` interface as well)

Basic rules of thumb for ```ArrayList``` and ```LinkedList```:
* ```ArrayList``` is like an array. Meaning that removing entries from the end is fast - internally only the length of the array is shortened. But adding or removing entries from the beginning is slow - internally this means copying all the remaining entries to a new array. If you only want to add or remove items in the end of your list, use ```ArrayList```. ```ArrayList``` manages array internally. Accessing elements by index is very fast. Adding item at the beginning takes long time because the items need to be shifted. Near to the end it is faster, because less elements need to be shifted.
* ```LinkedList```: this is based on doubly linked list data structure. If you want to add or remove items anywhere in the list, also in the middle, use ```LinkedList```. If you add items near the end of the list, ```ArrayList``` can be more efficient than ```LinkedList```. In ```LinkedList```, each element stores a reference to the previous and to the next element. To get an item at a particular index can be slower, because the list needs to iterate until that item. But adding an item anywhere is fast, because the links need to be changed, but shifting is not needed.
* ```Vector```: it is very similar to ```ArrayList```. The main differences are: (1) ```Vector``` is synchronized, ```ArrayList``` is not; (2) handling of growth of the stored data.
* ```Vector```: it is very similar to ```ArrayList```. The main differences are: 
  * ```Vector``` is synchronized, ```ArrayList``` is not
  * handling of growth of the stored data is different
* ```Stack```: inherited from ```Vector```.
> *Internally, both the ```ArrayList``` and ```Vector``` hold onto their contents using an ```Array```. When an element is inserted into an ```ArrayList``` or a ```Vector```, the object will need to expand its internal array if it runs out of room. A ```Vector``` defaults to doubling the size of its array, while the ```ArrayList``` increases its array size by 50 percent.*
>
>
* ```LinkedList``` also implements ```Queue``` interface
* ```ArrayBlockingQueue``` has a fix size which can be specified in the constructor

## Iterators
* Classical way: ```Iterator```
  * Can remove elements during iteration
  * Navigation forward only (```next()``` method)
* Modern way: foreach loop
  * Cannot change the list during iteration
* Alternative way: ```ListIterator```
  * Can change the list during iteration (```remove()```, ```set()```, ```add()```)
  * More methods (for example, ```hasPrevious```, ```previous```)
