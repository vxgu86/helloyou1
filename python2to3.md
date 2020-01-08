## 1 Python3中引入Queue会报出这个问题。

Python3中要这样引入：
import queue

Python2中要这样引入：
import Queue

为了兼容，可以这样写：
import sys
if sys.version > '3':
    import queue as Queue
else:
    import Queue

## 2 NameError:name ‘xrange’ is not defined
原因：

在Python 3中，range()与xrange()合并为range( )。
我的python版本为python3.5。
解决办法：

将xrange( )函数全部换为range( )。

## 3 生成器对象（generation object）运行以下代码时，遇到了一个错误：

    #定义生成器函数
    def liebiao():
    	for x in range(10):
    		yield x
    #函数调用
    g = liebiao()
     
    #打印元素
    print(g.next())

    D:\>python test.py
    Traceback (most recent call last):
      File "test.py", line 10, in <module>
        print(g.next())
    AttributeError: 'generator' object has no attribute 'next'

在python3.x版本中，python2.x的g.next()函数已经更名为g.__next__()，所以只需要将g.next()换成g.__next__()就可以了。如果你觉得g.__next__()太丑，使用next(g)也能达到相同效果。
https://blog.csdn.net/weixin_44316575/article/details/89258034


## 4 尝试将一个数字转换为Unicode。所以我尝试使用built-in function called ‘unichr‘，
>>> print repr(unichr(8224))

应输出：u'\u2020'

unichr(10000)

这个错误信息不断
NameError: name 'unichr' is not defined

在Python 3中，您只需使用chr：
>>> chr(10000)
'✐'

ord()函数是chr()函数（对于8位的ASCII字符串）或unichr()函数（对于Unicode对象）的配对函数，它以一个字符（长度为1的字符串）作为参数，返回对应的ASCII数值，或者Unicode数值，如果所给的Unicode字符超出了你的Python定义范围，则会引发一个TypeError的异常。

    ord是unicode ordinal的缩写,即编号
    chr是character的缩写,即字符
    ord和chr是互相对应转换的.
    但是由于chr局限于ascii,长度只有256,于是又多了个unichr.



