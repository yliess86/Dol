---
title: 'DOL Programming Language Specification'
date: '05/04/2020'
github: 'https://github.com/yliess86/Dol'
---

Dol Programming Language Specification
===

Dol is an experimental compiled data-oriented programming language. Its core concepts are inspired by languages such as Python, Jai and C. The philosophy of the language is to ensure pleasure of coding as well as performance by default. We hope to make this language useful for data driven applications carring about performance such as video games (ECS), data science, ... etc

```python
import math

Vec2: soa struct
    x: float
    y: float
    name: str = "unnamed"
    
Vec2 impl str: type
    return "Vec2({this.x}, {this.X}, {this.name})"
    
Vec2 impl magnitude: func () -> float
    return math.sqrt(this.x ** 2 + this.y ** 2)
    
v: Vec2 = Vec2(0.0, 2.0, name = "name")

print(v)             # Should output: Vec2(0.0, 2.0, "name")
print(v.magnitude()) # Should output: 2.0 
```

The language follows a simple rule, everything can be read intuitivly as plain english:
* `position: Vec2 = Vec2(1.0, 2.0)` 
    > Position is a Vec2 of value `Vec2(1.0, 2.0)`
* `Vec2: struct`
    > Vec2 is a struct
* `Vec2 impl foo: func (a: float) -> float`
    > Vec2 implement foo which is a function taking a of type float as argument and returning a float
* `for i: int in 0:10`
    > For i of type int in range 0 to 10

## Table of Contents

[TOC]

## Elements

Main syntaxic language components

### Comments

Comments are on a single line with `#`
E.g

```python
# comment
    # Another comment
codeee # comment
```

### Variables

Variables are **declared** by
`name: type`

And can be **initilized** 
`name: type = value`

And be **assigned** 
`name = value`

Every variable name written in **uppercase** will be considered as a **constant**
`PI: float = 3.14159265358979`

### Primitive Types

Primitive data types are

| Name  | Bits  | Bytes | Comment
|:------|------:|------:|:---
| bool  | 1     | N/A   | Simple boolean for conditional operations
| char  | 8     | 1     | Single character, signed
| uint  | 16    | 2     | Unsigned int
| int   | 32    | 4     | Signed integer
| float | 32    | 4     | Single precision floating point
| double| 64    | 8     | Double precision floating point

### Functions

Functions are implemented using the following syntax
```python
name: func (arg1: typearg1, arg2: typearg2) -> returntype
    # function body
    return returnvalue
```

Where `name` is a user defined string representing the function, `func` is a keyword, `typearg1` and `typearg2` are function types.

The returned element is given with the `return` **keyword**

There is no notion of `void` in this language. If a function doesn't return anything, one just have to remove the return type specification.

```python
noreturn: func (arg1: typearg1, arg2: typearg2)
    # function body
```

### Structures

Structures are the key elements of the language, they are the same as structures in C language: a contiguous memory area.

They can be defined with the syntax:

```python
name: layout struct
    VAR1
    VAR2
```

Where `struct` is a **keyword**, `name` is the name of the struct and `layout` is the kind of struct layout, either "" or "soa"

### Operators


#### Default operators

#### Operators Overloading

Every default binary and unary operator can be implemented for any struct.

```python
StructName impl  +: op (other: StructName) -> StructName
StructName impl  -: op (other: StructName) -> StructName
StructName impl  *: op (other: StructName) -> StructName
StructName impl **: op (other: StructName) -> StructName
StructName impl  /: op (other: StructName) -> StructName
StructName impl  >: op (other: StructName) -> StructName
StructName impl  <: op (other: StructName) -> StructName
StructName impl ==: op (other: StructName) -> StructName
StructName impl  &: op (other: StructName) -> StructName
StructName impl  |: op (other: StructName) -> StructName
```

Where `impl` is the **keyword** to assign a method to the struct `StructName` and `op` is the **descriptor** for the operator.

### Branching and conditions

#### Conditions

Branching can be achieve using the `if` and `else` **keywords**. Dol does not contain any notion of `elif` to avoid extensive use of condition branches often responsible for bad code pratices.

```python
if condition
    # Do something    
else
    # Do something else
```

#### Match

Dol propose the use of the **keyword** `match` as an alternative to `switch` in order to perform branching based on the value of a given variable.

```python
match variable
    value1
        # Do stuff
    value2
        # Do stuff
    default
        # Do default
```

The `default` **keyword** is used to specify a default behaviour.

### Loops

Two types of loops are available: `for` loops and `while` loops.
Their use is inplicit and resemble their Python equivalent.

`for variable: type in collection`
`while exit_condition`

**Range** based looping is also available using the `start:end:step` format.

```python
for i: int in 0:10
    print(i)
    
for i: int in 0:10:2
    print(i)
```

### Collections

#### Arrays


#### Lists

#### Dictionaries

### Memory management

### Error management

## Libraries

### Modules

### IO

### Math

### Network

### Automatic Distributed Computation

### Deep Learning huhu UwU
