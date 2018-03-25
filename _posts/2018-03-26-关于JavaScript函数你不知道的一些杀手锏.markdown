---
layout:     post
title:      "关于JavaScript函数你不知道的一些杀手锏"
subtitle:   "\"arguments还可以这样玩\""
date:       2018-03-26 10:57:00
author:     "stepday"
header-img: "img/post-bg-js-version.jpg"
catalog: true
tags:
    - JavaScript
---

## 前序
函数作为任何一门编程语言内编写和运用频次最高的概念，主要是得益于它能够进行封装多条语句独立实现一个功能或者一个业务点，它有着自己的作用域，且可在任何地方任何时候进行调用。

在对待函数参数这件事情上JavaScript采取了和其他语言不通的态度，JavaScript显得更加的开放，不限制传入参数的类型、个数。

## 正文
### 杀手锏一：arguments 你要用好
由于ECMAScript内部存储函数的参数是采用的数组形式，所以导致了JavaScript内函数参数的传递要求不会那么严格。举个栗子：
我们实现一个将传入的数据进行求和返回的函数，传入的参数个数不确定。

方法一：传入一个数组

```
/**
* 求和
* @params _arr:array 数据数组
*/
function sum(_arr){
   let _sum = 0;
   if(_arr){
       _arr.forEach(function(item){
           _sum += item;
       });
   }
   return _sum;
}

console.log(sum([1,2,3,4,5,6,7])); //28
```

方法二：巧用arguments

任何一个函数体内都自动定义了一个arguments变量来接收外部传入的函数参数，arguments结构和Array数组结构类似，有length属性和可以通过下标来提取第i个参数值；

```
/**
* 求和
*/
function sum(){
   let _sum = 0;
   if(arguments){
       for(let i = 0;i<arguments.length;i++){
           _sum += arguments[i];
       }
   }
   return _sum;
}
console.log(sum(1,2,3,4,5,6,7)); //28
```
> 如果想让arguments和Array拥有一样的特性，可以借助Array的slice来进行转换，转换代码如下所示：

```
var _arr = Array.prototype.slice.apply(arguments);
```


## 感悟
- JavaScript内函数的参数不是必需的，命名的参数只是提供便利，提升语义化理解；

==未完，待续....==
