# 118 pascal triangle(杨辉三角)

```python
# 用排列组合 计算出 每项的值
from scipy.special import comb
def generate(self, n):
    rows = []
    for i in range(n):
        row = []
        # len=row_index+1，行号从0开始
        for j in range(i+1):
            row.append(int(comb(i, j)))
        rows.append(row)
    return rows
```

119: 打印杨辉三角第n行(第n行第二个数是n)

```python
def getRow(self, n):
    row = []
    for i in range(n+1):
        row.append(int(comb(n, i)))
    return row
```

## 用generator生成杨辉三角
```python
# 性能：前10%
def triangles():
    b = [1]
    while True:
        yield b
        c = [0] + b
        d = b + [0]
        b = list(map(lambda x,y:x+y, c, d))

# 简短点
def getRow(self, n):
    b = [1]
    for i in range(n):
        b = [1]+[ b[i]+b[i+1] for i in range(i) ]+[1] # i==(len(b)-1)
    return b
```
<pre>
杨辉三角的递推思路
  b(n) = 0  b1 b2 ... bn-1 bn
    +d = b1 b2 b3 ... bn   0
= b(n+1) = b.next  
</pre>
