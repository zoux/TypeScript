# 介绍

至ECMAScript 2015开始，`symbol`成为了一种新的原始类型，就像`number`和`string`一样。

`symbol`类型的值是通过`Symbol`构造函数创建的。

```ts
let sym1 = Symbol();

let sym2 = Symbol("key"); // 可选的字符串key
```

Symbols是不可改变的且唯一。

```ts
let sym2 = Symbol("key");
let sym3 = Symbol("key");

sym2 === sym3; // false, symbols是唯一的
```

像字符串一样，symbols也可以被用做对象属性的键。

```ts
let sym = Symbol();

let obj = {};

obj[sym] = "value";
console.log(obj[sym]); // "value"
```

Symbols也可以与计算出的属性名声明相结合来声明对象的属性和类成员。

```ts
const getClassNameSymbol = Symbol();

class C {
    [getClassNameSymbol](){
       return "C";
    }
}

let c = new C();
let className = c[getClassNameSymbol](); // "C"
```

# 大家熟悉的Symbols

除了用户定义的symbols，还有一些已经熟悉的内置symbols。
内置symbols用来表示语言内部的行为。

下面是这样一些symbols的示例：

## `Symbol.hasInstance`

这个方法是构造器对象用来识别一个对象是否是其实例。会被`instanceof`运算符调用。

## `Symbol.isConcatSpreadable`

布尔值，表示当在一个对象上调用`Array.prototype.concat`时，这个对象的数组元素是否可展开。

## `Symbol.iterator`

一个方法返回对象的默认迭代器。被`for-of`语句调用。

## `Symbol.match`

正则表达式方法用来匹配字符串。被`String.prototype.match`调用。

## `Symbol.replace`

正则表达式方法用来替换字符串中匹配的子串。被`String.prototype.replace`调用。

## `Symbol.search`

正则表达式方法返回匹配上的部分在字符串中的索引。被`String.prototype.search`调用。

## `Symbol.species`

值为一个构造函数，用来创建对象实例。

## `Symbol.split`

正则表达式方法来用分割字符串。
被`String.prototype.split`调用。

## `Symbol.toPrimitive`

把对象转换为相应的原始值。
被`ToPrimitive`抽象操作调用。

## `Symbol.toStringTag`

字符串用来创建对象默认的字符串描述。
被内置方法`Object.prototype.toString`调用。

## `Symbol.unscopables`

一个对象，它自己拥有的属性会被`with`作用域排除在外。