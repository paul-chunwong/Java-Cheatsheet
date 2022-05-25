# Java-Cheatsheet

---------------------------------------------------------------------------------------------------------------------
Shortcuts in IntelliJ IDEA:

sout -> tab              // System.out.println()
psvm -> tab              // public static void main(String[] args){...}
Option + Command + L     // Auto Format
Edit -> Find -> Replace  // can replace all the same word in the class together

How to quickly create abstract class for the current class:
Refactor -> Extract Superclass -> rename the super class
-> select the methods that have same signature and implementations (comparing to other same level classes)
-> select the methods that have same signature but not the same implementations with Make Abstract (comparing to other same level classes)

How to quickly create try/catch:
Highlight the code -> Code -> Surrounded with -> try/catch


---------------------------------------------------------------------------------------------------------------------
String:

\n
配合String内使用可以隔行（类似println）
System.out.println("\n\n");        -> 隔三行

\t
配合String内使用可以留白
\"
在String内使用 并实际在console输出\后面的char 例子："

"abC".equalsIgnoreCase("aBc");  -> return true
"abC".equals("aBC");            -> return false
"abC".substring(0, 1);          -> return "a"


---------------------------------------------------------------------------------------------------------------------
Common things:

&& -> AND
|| -> OR
!  -> NOT


---------------------------------------------------------------------------------------------------------------------
Date Type:

Primitive types:
int, double, String, char, boolean, short, float(e.g. 3.1423f), long(e.g. 321975345897L)
如果一个data type的第一个字母是大写 那这个data type就是reference: e.g. String

Integer.parseInt("abc");     -> parse String to int
Double.parseDouble("abc");   -> parse String to Double
Integer.toString(12);        -> parse int to String
Integer.toHexString(12);     -> parse int to Hex String



---------------------------------------------------------------------------------------------------------------------
User Input:

1) import java.util.Scanner;
2) Scanner scanner = new Scanner(System.in);
3) String s1 = scanner.nextLine();
3) String s2 = scanner.next();         // store only one character in the String
3) int n1 = scanner.nextInt();         // should use scanner.nextLine() in the next line
3) double n2 = scanner.nextDouble();
3) char c1 = scanner.next();
4) scanner.close();

After using nextInt & etc. we should use scanner.nextLine(); to clear the scanner,
otherwise error will occur when using nextLine() later.


---------------------------------------------------------------------------------------------------------------------
Expression and Math Functions:

int / int     -> 只会出最接近的整数
10 / 3        -> 3
10 % 3        -> 1

double / int  -> 会出小数点
10.0 / 3.0    -> 3.333333

Math.max(3.14, -10)   -> 3.14
Math.min(3.14, -10)   -> -10
Math.abs(-11)         -> 11
Math.sqrt(16)         -> 4
Math.round(3.14)      -> 3.0
Math.ceil(3.14)       -> 4.0
Math.floor(3.14)      -> 3.0


---------------------------------------------------------------------------------------------------------------------
Random Values:

1) import java.util.Random;
2) Random random = new Random();
3) int x1 = random.nextInt(6);          -> 0(inclusive) - 5(inclusive)
3) int x2 = random.nextInt(6) + 1;      -> 1(inclusive) - 6(inclusive)
3) double y1 = random.nextDouble();     -> 0.0 - 1.0
3) boolean z = random.nextBoolean();    -> true or false


---------------------------------------------------------------------------------------------------------------------
GUI Intro:

1) import javax.swing.JOptionPane;
2) String name = JOptionPane.showInputDialog("Enter your name");   // popup window that asks input
3) JOptionPane.showMessageDialog(null, "Hello " + name);           // display window that shows name


---------------------------------------------------------------------------------------------------------------------
Object:

Dog d;
d = new Dog();    (Dog d = new Dog();)
Dog fido = d;

fido is not copy of d, they are now pointing to the same Dog object,
Any change happened in fido or d will now change the other (because they are the same Dog object now).
Passing an object into the method as parameter will not copy a new object; instead, it points to the same object.
When passing objects into different connect methods, carefully consider their scope.


object1.equals(object2)      -> return true if two objects are same, false otherwise
object1 == object1           -> return true if two objects have same memory address, false otherwise


---------------------------------------------------------------------------------------------------------------------
Primitive Array:

int[] nums = {2,7,11,15};
nums[2]     -> return 11
nums.length -> return 4


---------------------------------------------------------------------------------------------------------------------
ArrayList<type>:

List<>          // List interface, cannot be instantiated
ArrayList<>     // subclass of List, can be instantiated
LinkList<>      // subclass of List, can be instantiated


import java.util.ArrayList;                     // when using ArrayList<type>

ArrayList<Dog> dogs = new ArrayList<Dog>();     // ArrayList<type> is an object
dogs.add(d);                                    // and the type must be object, cannot be primitive like int

LinkList<Dog> dogs = new LinkList<Dog>();
List<Dog> dogs = new List<Dog>();               // DO NOT WORK!! since List is an interface
List<Dog> dogs = new ArrayList<Dog>();
List<Dog> dogs = new LinkList<Dog>();


arrayList1.add("a")      -> add "a" into the list
arrayList1.get(1)        -> return the value of second item in the list
arrayList1.size()        -> return size of list
arrayList1.isEmpty()     -> return true if list is empty, otherwise return false
arrayList1.contains(1)   -> return true if list has 1, otherwise return false


---------------------------------------------------------------------------------------------------------------------
HashSet:
// a HashSet is a collection of objects where every object is unique

Set<>          // Set interface, cannot be instantiated
HashSet<>      // subclass of Set, can be instantiated

import java.util.HashSet;                        // import statement

HashSet<Car> cars = new HashSet<Car>();          // HashSet<type> is an object
cars.add(c);                                     // and the type must be object, cannot be primitive like int

Set<Car> cars = new Set<Car>();                  // DO NOT WORK!! since Set is an interface
Set<Car> cars = new HashSet<Car>();

hashSet1.add("a")       -> add "a" into the set
hashSet1.add(c1)        -> add object c1 into the set
hashSet1.remove(c1)     -> remove object c1 from the set
hashSet1.size()         -> return size of set
hashSet1.contains(c1)   -> return true if set contains object c1, otherwise return false


---------------------------------------------------------------------------------------------------------------------
Testing:

1) import static org.junit.jupiter.api.Assertions.*;
2) assertTrue(true);                    -> pass
2) assertFalse(false);                  -> pass
2) assertTrue(false);                   -> fail
2) assertFalse(true);                   -> fail
2) assertEquals("000000", "000000");    -> pass
2) assertEquals("000000", "111111");    -> fail
2) assertEquals(dog1, dog2);            -> DO NOT USE!! Because they are comparing the memory address, not the value.


Test class example:

import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

class SomeClassTest{
    private SomeClass sc;

    @BeforeEach
    public void runBefore(){
        sc = new SomeClass();
    }

    @Test
    public void testMethod1(){
        sc.method1();
        assertEquals(xxxxxxx);
        assertTrue(xxxxxxx);
        assertFalse(xxxxxxx);
    }

    @Test
    public void testMethod2(){
        sc.method12();
        assertEquals(xxxxxxx);
        assertTrue(xxxxxxx);
        assertFalse(xxxxxxx);
    }
}
