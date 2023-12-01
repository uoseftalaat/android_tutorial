# Kotlin [Docs](https://kotlinlang.org/docs/getting-started.html)
programming language used in :
- Android Apps
- Cross-platform mobile apps
- frontend web apps
- backend apps

## Why Kotlin?(Android)
- Easy learning
-  help avoiding common programming mistakes (null safety)
-  Interoperability with Java
-  Less code combined with greater readability.
-  Support for multiplatform development
## Where to write Kotlin?
- Android Studio
- Intellij
  
## Basic syntax

### Entry point 
``` Kotlin
fun main() {
    println("Hello world!")
}
```
or 
``` Kotlin
fun main(args: Array<String>) {
    println(args.contentToString())
}
```

### Variables
#### Declaration

    [val/var] var_name [:type](optional) 
``` Kotlin
val a: Int = 1
val b = 2
val c: Int
var x = 5
```

#### val
>Read-only local variables are defined using the keyword val. They can be assigned a value only once.

``` Kotlin
val a: Int = 1  // immediate assignment
val b = 2   // `Int` type is inferred
val c: Int  // Type required when no initializer is provided
c = 3       // deferred assignment
c = 5       //error! 
```

### var 
> Variables that can be reassigned use the var keyword.

``` Kotlin
 var x = 5 // `Int` type is inferred
     x += 1
```
## Arrays
#### Declaration
```kotlin
//creating array using constructor
val arr = Array(5) { i -> (i * i).toString() } 
val arr = Array(5, { i -> i * 1 })
var arr = IntArray(5) { it * 1 }

//using arrayof
val num = arrayOf(1, 2, 3, 4)   //implicit type declaration
val num = arrayOf<Int>(1, 2, 3) //explicit type declaration 
```
### Accessing and modifying arrays
```kotlin
    //using get and set
    val x = num.get(0)
    num.set(1,3) //The set() method takes 2 parameters: the index of the element and the value to be inserted.
    //Using the index operator [ ] 
    val x = num[0]
    num[1]=3    
```
## Control flow

### If expression:
> note: if is an expression: it returns a value.

#### syntax
    if(Condition){ lines / expression}
    if else (Condition){ lines / expression}
    else {lines / expression}

``` Kotlin
var max = a
if (a < b) max = b

// With else
var max: Int
if (a > b) {
    max = a
} else {
    max = b
}
```
> note:if you're using if as an expression, for example, for returning its value or assigning it to a variable, the else branch is mandatory.
```kotlin 
// As expression
val max = if (a > b) a else b
```

### When expression
> Like Switch Statements in java

``` Kotlin
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> {
        print("x is neither 1 nor 2")
    }
}
```
> Error if there is uncovered value 

### For Loop
``` kotlin
// To iterate over a range of numbers
// from 1 to 3
for (i in 1..3) {
    println(i)
}
// from 6 to 0
for (i in 6 downTo 0) {
    println(i)
}
// decrease by 2 (steps)
for (i in 6 downTo 0 step 2) {
    println(i)
}

// iterating over arrays or lists
for (i in array) {
    println(i)
}
for (i in array.indices) {
    println(array[i])
}
for ((index, value) in array.withIndex()) {
    println("the element at $index is $value")
}
```

### While Loops
``` Kotlin
while (x > 0) {
    x--
}

do {
    val y = retrieveData()
} while (y != null) // y is visible here!
```
### Foreach
```kotlin
var arr = ArrayOf(1,2,3)
arr.forEach {
   println(it)
}
```
## Null safety
Kotlin's type system is aimed at eliminating the danger of null references, also known as The Billion Dollar Mistake

we cannot write ``` var a=null ``` in kotlin

To allow nulls, you can declare a variable as a nullable string by writing String?:
``` kotlin
var b: String? = "abc" // can be set to null
b = null // ok
```
### Checking for null in conditions
``` kotlin
val b: String? = "Kotlin"
if (b != null && b.length > 0) {
    print("String of length ${b.length}")
} else {
    print("Empty string")
} 
```
### Safe calls
Your second option for accessing a property on a nullable variable is using the safe call operator ?.
``` kotlin
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) // Unnecessary safe call 
```
To perform a certain operation only for non-null values, you can use the safe call operator together with let
``` kotlin
val listWithNulls: List<String?> = listOf("Kotlin", null)
for (item in listWithNulls) {
    item?.let { println(it) } // prints Kotlin and ignores null
}
```
### Elvis operator ( ?: )
if b is null then l=-1
``` Kotlin
val l = b?.length ?: -1 
```
 
### The !! operator
>Thus, if you want an NullPointerExeption, you can have it, but you have to ask for it explicitly and it won't appear out of the blue.

``` kotlin
val l = b!!.length 
```


## Function
### Lambda expressions
> unctions that are not declared but are passed immediately as an expression
``` kotlin
 val sum: (Int, Int) -> Int = { x: Int, y: Int -> x + y } 
 val sum = { x: Int, y: Int -> x + y }
 ```
 - A lambda expression is always surrounded by curly braces.
 - Parameter declarations in the full syntactic form go inside curly braces and have optional type annotations.
 - The body goes after the ->.
 - If the inferred return type of the lambda is not Unit, the last (or possibly single) expression inside the lambda body is treated as the return value.


### Function in Kotlin


- Kotlin functions are declared using the fun keyword
  ``` kotlin 
  fun double(x: Int): Int {
    return 2 * x
    } 
  ```
- Function parameters are defined using Pascal notation - name: type. Parameters are separated using commas, and each parameter must be explicitly typed
    ``` kotlin
    fun powerOf(number: Int, exponent: Int): Int { /*...*/ }
    ```
- Function parameters can have default values
  ``` kotlin
  fun read(
        b: ByteArray,
        off: Int = 0,
        len: Int = b.size,
    ) { /*...*/ }
    ```
- If a function does not return a useful value, its return type is Unit (Unit return type declaration is also optional).
  ```kotlin
  fun printHello(name: String?): Unit {
        if (name != null)
            println("Hello $name")
        else
            println("Hi there!")
        // `return Unit` or `return` is optional
    }
  ```
- When a function returns a single expression, the curly braces can be omitted and the body is specified after a = symbol.
    ``` kotlin
    fun double(x: Int): Int = x * 2     
    ```
- If the last argument after default parameters is a lambda, you can pass it either as a named argument or outside the parentheses.
    ``` kotlin
        fun foo(
        bar: Int = 0,
        baz: Int = 1,
        qux: () -> Unit,
    ) { /*...*/ }

    foo(1) { println("hello") }     // Uses the default value baz = 1
    foo(qux = { println("hello") }) // Uses both default values bar = 0 and baz = 1
    foo { println("hello") }        // Uses both default values bar = 0 and baz = 1
    ```

## Classes
#### Declaration
``` kotlin
class Person constructor(firstName: String) { /*...*/ }
```
#### notes:-
1. A class in Kotlin can have a primary constructor and one or more secondary constructors
1. he primary constructor is a part of the class header
1. if the primary constructor does not have any annotations or visibility modifiers, the constructor keyword can be omitted like :

    ``` kotlin
        class Person private constructor(firstName: String) { /*...*/ }
        class Customer public @Inject constructor(name: String) { /*...*/ }
    ```
1. using val/var in Primary constructor tells that the variables not only arguments for the Primary constructor but fields for the class 
    ``` kotlin
        class Person(
            val firstName: String,
            val lastName: String,
            var age: Int
        ) { /*...*/ }
   ```
   arguments here is also used as field in the class 

### the initializer blocks
> The primary constructor cannot contain any code. Initialization code can be placed in initializer blocks prefixed with the init keyword.

>During the initialization of an instance, the initializer blocks are executed in the same order as they appear in the class body, interleaved with the property initializers

``` kotlin
    class InitOrderDemo(name: String) {
        val firstProperty = "First property: $name".also(::println)
        
        init {
            println("First initializer block that prints $name")
        }
        
        val secondProperty = "Second property: ${name.length}".also(::println)
        
        init {
            println("Second initializer block that prints ${name.length}")
        }
    }
    //output
    /*
    First property: hello
    First initializer block that prints hello
    Second property: 5
    Second initializer block that prints 5
    */
```

### Secondary constructor 
```kotlin
class Person(val name: String) {
    val children: MutableList<Person> = mutableListOf()
    constructor(name: String, parent: Person) : this(name) {
        parent.children.add(this)
    }
}
```
### companion Object 
> like static in java 

``` kotlin
class ToBeCalled {
    companion object Test {
        var someInteger: Int = 10
        fun callMe() = println("You are calling me :)")
    }
}
fun main(args: Array<String>) {
    ToBeCalled.callMe()
    print(ToBeCalled.someInteger)
}
```

### Inheritance
- All classes in Kotlin have a common superclass Any
- A class that is neither abstract nor open is considered to be final and can not be extended.
``` kotlin 
open class Base(p: Int)
class Derived(p: Int) : Base(p)
```
- The override modifier is required for every overrided fun 
- If there is no open modifier on a function declaring a method with the same signature in a subclass is not allowed
``` kotlin
open class Shape {
    open fun draw() { /*...*/ }
    fun fill() { /*...*/ }
}

class Circle() : Shape() {
    override fun draw() { /*...*/ }
} 
```

- If the derived class has no primary constructor, then each secondary constructor has to initialize the base type using the super

``` kotlin
class MyView : View {
    constructor(ctx: Context) : super(ctx)
    constructor(ctx: Context, attrs: AttributeSet) : super(ctx, attrs)
}
```

### Getters and setters for Properties

The full syntax for declaring a property is as follows:
      
    var <propertyName>[: <PropertyType>] [= <property_initializer>]
    [<getter>]
    [<setter>]
if you define a custom getter/setter, it will be called every time you access the property 
``` kotlin 
class Rectangle(val width: Int, val height: Int) {
    val area: Int // property type is optional since it can be inferred from the getter's return type
        get() = this.width * this.height
}
var stringRepresentation: String
    get() = this.toString()
    set(value) {
        setDataFromString(value) // parses the string and assigns values to other properties
    }
```
### Visibility modifiers
- public 
- protected
- internal (it’ll be available in the same module only)
- private
## Some idoms
### Lazy property
> he value is computed only on first access compute the string
``` kotlin
number?.let { var aq : Int = it} 
``` 
### singleton
``` koltin
object Resource {
    val name = "Name"
}
```
### With
> Call multiple methods on an object instance 
``` kotlin
class Turtle {
    fun penDown()
    fun penUp()
    fun turn(degrees: Double)
    fun forward(pixels: Double)
}

val myTurtle = Turtle()
with(myTurtle) { //draw a 100 pix square
    penDown()
    for (i in 1..4) {
        forward(100.0)
        turn(90.0)
    }
    penUp()
}
```
### Apply
> Configure properties of an object
``` kotlin
val myRectangle = Rectangle().apply {
    length = 4
    breadth = 5
    color = 0xFAFAFA
} 
```

















