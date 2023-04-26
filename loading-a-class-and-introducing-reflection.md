# Using Java's `Class.forName(…)` and Introducing Reflection

To load a class dynamically at runtime, you will use `Class.forName()`.

You will load a class using its fully qualified name and perform operations on the created instance. Follow these steps:

1. Create a new Java class named `DynamicClassLoadingDemo`.

2. Add a main method to the class.

3. In the main method:

   1. Load a class dynamically using its fully qualified name by calling `Class.forName("classNameToLoad")`. For this exercise, load the `java.util.LinkedList` class.
   2. Assign the return value to a variable of type `Class<?>`. For example, `Class<?> loadedClass = Class.forName(...);`
   3. Handle the `ClassNotFoundException` by printing an error message.

4. Now you've loaded the class, you can use it to create an instance.

   1. To do this, ask the class object for its default constructor (`loadedClass.getDeclaredConstructor()`), then invoke the `newInstance()` method on what it returns (ie the constructor instance).
   2. Handle the `InstantiationException` and `IllegalAccessException` exceptions by printing an error message.

5. Cast the created instance to the `java.util.List` interface if it is an instance of it. You now have a `List` instance, so you can perform some operations on the list object as you would normally. For example, add a few elements to the list and print its contents (eg `list.add("Hello");` etc).

6. Run your code and ensure that it works!

---

## Detailed Steps

Here are more detailed steps if you need some extra help:

1. Create a new Java class named `DynamicClassLoadingDemo`.

2. Add a main method to the class:

   ```java
   public static void main(String[] args) {
       // Your code will go here
   }
   ```

3. Load a class and handle the `ClassNotFoundException`:

   ```java
   try {
       // Load the desired class using its fully qualified name
       Class<?> loadedClass = Class.forName("java.util.LinkedList");
   } catch (ClassNotFoundException e) {
       System.err.println("Class not found: " + e.getMessage());
   }
   ```

4. Now you've loaded the class, you can use it to create an instance:

   ```java
   try {
       // Load the desired class using its fully qualified name
       Class<?> loadedClass = Class.forName("java.util.LinkedList");

       // Create an instance of the loaded class
       Object instance = loadedClass.getDeclaredConstructor().newInstance();
   } catch (ClassNotFoundException e) {
       System.err.println("Class not found: " + e.getMessage());
   } catch (InstantiationException | IllegalAccessException | NoSuchMethodException | InvocationTargetException e) {
       System.err.println("Error creating an instance: " + e.getMessage());
   }
   ```

5. Add elements to the list and print its contents. You can do this inside your `try…catch` block:

   ```java
       // Cast the instance to a known interface or superclass, if applicable
       if (instance instanceof java.util.List) {
           java.util.List list = (java.util.List) instance;

           // Perform operations on the list object
           list.add("Hello");
           list.add("Java");

           // Print the list's content
           System.out.println("List content: " + list);
       }
   ```

6. Run your code and ensure that it works!

---

## Summary of Example

Here's the whole content of `main()`:

```java
try {
    // Load the desired class using its fully qualified name
    Class<?> loadedClass = Class.forName("java.util.LinkedList");

    // Create an instance of the loaded class
    Object instance = loadedClass.getDeclaredConstructor().newInstance();

    // Cast the instance to a known interface or superclass, if applicable
    if (instance instanceof java.util.List) {
        java.util.List list = (java.util.List) instance;

        // Perform operations on the list object
        list.add("Hello");
        list.add("Java");

        // Print the list's content
        System.out.println("List content: " + list);
    }
} catch (ClassNotFoundException e) {
    System.err.println("Class not found: " + e.getMessage());
} catch (InstantiationException | IllegalAccessException | NoSuchMethodException | InvocationTargetException e) {
    System.err.println("Error creating an instance: " + e.getMessage());
}
```
