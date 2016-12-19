#Dev Tools Notes
Notes from Day #9 of Javascript 30: Dev Tools Domination

### Break on...
* subtree modifications
* attribute modifications
* node removal

Allows you to easily find where in a script a particular DOM action is happening. Adds a debugging break point.

___
### `console.` stuff
* `console.warn()` — gives a warning (yellow highlighting with stack trace of where the violation occured)
* `console.error()` — displays an error with stack trace
* `console.info()` — blue info icon
* `console.assert( assertation, errorMessage )` — only fires if assertation evaluates falsy. Lets you test for things.
*  `console.clear()` — clears the console
*  `console.dir()` — logs the DOM element
*  `console.group()` / `console.groupEnd()` — by bookending a group of console calls with `console.group( groupLabel )` and `console.endGroup(groupLabel )`, you log your groups all tidy with code folding. the "groupLabel" passed in to both is a **string** that lables the group

```js
dogs.forEach(dog => {
  console.group( `${dog.name}` )
    console.log( `this is ${dog.name}`)
    console.log(`${dog.name} is ${dog.age} years old`);
    console.log(`${dog.name} is ${dog.age * 7} dog years old`);
  console.groupEnd(`${dog.name}`)
})
```
* you can sub `group()` for `groupCollapsed()` and the group will be logged with the code folded by default, which might be a lot more useful if you're logging a lot of groups. That just looks like 

```js
dogs.forEach(dog => {
  console.groupCollapsed( `${dog.name}` )
    console.log( `this is ${dog.name}`)
    console.log(`${dog.name} is ${dog.age} years old`);
    console.log(`${dog.name} is ${dog.age * 7} dog years old`);
  console.groupEnd(`${dog.name}`)
})
```
* `console.count()` — logs a count of how many times...

* `console.time(label)` and `console.timeEnd(label)` — bookending code with these logs the ammount of time the process took

```js
  console.time('fetching data')
    fetch('https://api.github.com/users/travisgorman')
      .then(data => data.json())
        .then(data => {
          console.timeEnd('fetching data')
          console.log( data )
        });


    // -> fetching data: 33.422ms
    // -> { Object }
```
* `console.table( arrayOfObjects )` — takes an array of objects and logs it as a table.

___
### String interpolation
* `%s` — allows you to interpolate a variable, as in

```js
console.log( 'that %s was big', 'string' );
```
* although you might prefer using ES6 backticks and `${}`

```js
let wee = 'GO!';
console.log(`ready, get set, ${wee}`)
```
___
### You can style console logs (if you want...)
* `%c` — allows you to style log printouts, as in

```js
console.log('%c This string is big', 'font-size:50px');
```




