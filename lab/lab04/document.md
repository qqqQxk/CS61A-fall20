# Lab 4

## Tree Recursion

### Q4:

1. 当只有一行或者只有一列时行动方法只有一种
2. 有m行n列时，需要移动到(m,n-1)或者(m-1,n)的位置,之后再踏入(m,n),可以保证中间的路线不会有重叠也不会有遗漏

```python
if m == 1 or n == 1:
    return 1
else:
    return paths(m - 1, n) + paths(m, n - 1)
```



### Q5:

题目给的提示是考虑使用最后一位或不使用

1. 当t<=0或n<=0时,没有最大数字,返回0
2. 之后考虑使用最后一位,如n = 20125,t = 3,那么剩下的就是n = 2012,t = 2,接下来就可以使用递归来完成这个过程,注意最后要再加上5
3. 考虑不使用最后一位,那么n = 2012,t = 3,仍然是递归,在返回时选择2,3当中的最大者

```python
if t <= 0 or n <= 0:
    return 0
else:
    return max(max_subseq(n // 10,t - 1) * 10 + n % 10, max_subseq(n // 10,t))
```



### Q6:

题目要求从前向后比对字符串w1和w2,并依次记录需要添加的字母

1. 每次比对w1[0] 和 w2[0],如果相同,继续向下比对
2. 如果不同,说明w2[0]需要纳入记录中,然后比对w1[0]和w2[1]
3. 比对到最后w1空了,w2不空,剩余的w2都需纳入记录中
4. 比对到最后w1,w2都空了,直接返回空

```python
if w1 == '' and w2 != '':
    return w2
if w2 == '':
    return ''
if w1[0] != w2[0]:
    return w2[0] + add_chars(w1,w2[1:])
else:
    return add_chars(w1[1:],w2[1:])
```
