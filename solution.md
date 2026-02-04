## Solution to Problem 1

(a)

At line 4, pi is bound to the value in line 3.
At line 7, pi is bound to the value in line 1.

(b)

In line 3, x is bound to the parameter declared in line 2.
In line 6, it is bound to x declared in line 5.
In line 10, it is bound to the x declared in line 5.
Both uses of x in line 11 are bound to x in line 1.

## Solution to Problem 2

(a) Execution trace:

```
pow(2, 3)
if 3 > 0 then 2 * pow(2, 3 - 1) else 1
if true then 2 * pow(2, 3 - 1) else 1
2 * pow(2, 3 - 1)
2 * pow(2, 2)
2 * (if 2 > 0 then 2 * pow(2, 2 - 1) else 1)
2 * (if true then 2 * pow(2, 2 - 1) else 1)
2 * (2 * pow(2, 2 - 1))
2 * (2 * pow(2, 1))
2 * (2 * (if 1 > 0 then 2 * pow(2, 1 - 1) else 1))
2 * (2 * (if true then 2 * pow(2, 1 - 1) else 1))
2 * (2 * (2 * pow(2, 0)))
2 * (2 * (2 * (if 0 > 0 then 2 * pow(2, 0 - 1) else 1)))
2 * (2 * (2 * (if false then 2 * pow(2, 0 - 1) else 1)))
2 * (2 * (2 * 1))
2 * (2 * 2)
2 * 4
8
```

(b) Tail-recursive implementation

```scala
def powTail(x: Int, n: Int): Int =
  def loop(acc: Int, i: Int): Int =
    if i > 0 then loop(acc * x, i - 1) else acc
  loop(1, n)
```

Execution trace:

```
powTail(2, 3)
loop(1, 3)
if 3 > 0 then loop(1 * 2, 3 - 1) else 1
if true then loop (1 * 2, 3 - 1) else 1
loop(1 * 2, 3- 1)
loop(2, 2)
if 2 > 0 then loop(2 * 2, 2 - 1) else 2
if true then loop(2 * 2, 2 - 1) else 2
loop(2 * 2, 2 - 1)
loop(4, 1)
if 1 > 0 then loop(4 * 2, 1 - 1) else 4
if true then loop(4 * 2, 1 - 1) else 4
loop(4 * 2, 1 - 1)
loop(8, 0)
if 0 > 0 then loop (8 * 2, 0 - 1) else 8
if false then loop (8 * 2, 0 - 1) else 8
8
```