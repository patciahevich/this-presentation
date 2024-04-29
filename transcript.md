Hi, my name is Volha. And the theme of my presentation is ‘this concept in JavaScript’

Let's start by defining what the this keyword is. 
As we all know, in JavaScript all data types and structures, except primitive ones, are descendants of an object. And the this keyword always refers to an object. In the other words, the value of this is the object “before dot”, which used to call the method.
The value of this is evaluated during the run-time, depending on the context. And this is an interesting part.

To fully understand this concept, I suggest taking a look how we can execute code in JavaScript.

We can call the function. In this case this will be equal to the global object (for example window if we run the JS code in the browser).
In nested functions we will get the same result
But if we use “use strict” mode, this will be equal undefined.

Call a function as a method of an object. In this case this will be a reference to this object. 

We are able to invoke the constructor function (a function that we use to create objects of the same type and call using the new keyword). When called this way, this matches the object we constructed. 
How does it work? 
- function initiates an object
- this object is assigned to this
- function body is executed
- the value of this is returned.

And the last way to execute code is indirect function call.
As I said before, in JS this is not related to a single object, but is determined during code execution. However, sometimes we want this to refer to a specific object.
And JavaScript provides three native methods that can be used to manipulate the way the this keyword behaves. They kind of bind the context to the function. Let's look at them.

Call and apply methods call a function with passed context as a first argument. We also can pass another function arguments futher separated by commas (when we use call method) or as an array (if we use apply method)
Bind will return a new function, without executing it. Note that bind changes the context once. This method cannot be called again.

Also in non–strict mode, if a function is called with a this value that's not an object, the this value is substituted with an object. Null and undefined become globalThis. 
Primitives  are converted to an object using the related constructor, so the primitive number 7 is converted to a Number wrapper class and the string 'foo' to a String wrapper class.


Losing this.
There are scenarios where this differs from what we expect. For example, I pass an object's method as a parameter of a setTimeout function. When the function is executed it will take this from the global object (or undefined), but not from the user object as I expect.
How to fix that?
- Don’t use this if it’s possible.
- Wrap the call in an anonymous function by creating a closure. Then the function will take this from the outer function
- Call a method with clear context passing (using call and apply methods)
- Bind context using bind method. But remember that you cannot change the context later
This way, a fixed context is used, and the method is called with what it needs, rather than attempting to be called from another object.

Now some strings on the finger

1.	When using this in an event listener, this will refer to the DOM element that fired the event.
2.	In nested objects the this keyword refers to the object whose method call it.
3.	If the method is in the prototype chain, then this refers to the object on which the method was called, i.e. as if the method were a method of the object itself, and not a prototype.
4.	Arrow functions don’t have their “own” this. 

If we reference this from such a function, it’s taken from the outer parent function. So, we can write the code from the previous example this way. The only problem of using arrow functions  is that we tend to lose the function name. Sometimes it makes sense.

Wrapping Up
Flexible this in JavaScript is both a blessing and an evil. On the one hand, we can define abstract functions that will be run within their context. However, as we saw today this can lead to coding problems.

Thank you for your time. Bye.

