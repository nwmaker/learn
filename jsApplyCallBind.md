# Apply, Call, and Bind in JavaScript

## Apply: Function.prototype.apply()

The apply() method calls a function with a given this value, and arguments provided as an array or array-like object.

```
const numbers = [5, 6, 2, 3, 7]

// Math is one of the standard built-in objects
const maxNum = Math.max(...numbers) // returns the largest of zero or more numbers

const maxNumA = Math.max.apply(null, numbers) // Apply takes an Array
```

## Call: Function.prototype.call()

The call() method calls a function with a given this value and arguments provided individually.

```
function P(name, price) {
  this.name = name
  this.price = price
}

function F(name, price) {
  P.call(this, name, price) // this and argument list instead of an array of arguments
  this.category = 'food'
}

console.log(new F('cheese', 5).name)
```

## Bind: Function.prototype.bind()

```
let testing = {
  x: 36,
  getX: function() { return this.x; }
}

console.log(testing.getX()) // 36

const rX = testing.getX
console.log(rX()) // undefined

const gX = rX.bind(testing)
console.log(gX()) // 36
```
But if the arrow function is used in testing, that this is bound to the global, e.g. in the browser, that this is Window.


```
function list() {
  return Array.prototype.slice.call(arguments);
}

const list1 = list(1, 2, 3, 4)

const leading36List = list.bind(null, 36)
const list2 = leading36List()
const list3 = leading36List(2, 3, 4)
```

## Reference
* [MDN bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

