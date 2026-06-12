---
title: "error running jython with  processing script"
date: 2009-05-25
forum: Multimedia Software
---

### Post by bobdobbs on 2009-05-25
Has anyone gotten processing and jython working together on ubuntu?

I've decided to start learning python. 
I also decided to start experimenting with processing.

I discovered that it is possible to create processing animations with python, via jython.

However, when I run jython on a simple python processing script, I get this error:

```

raceback (innermost last):
  (no code object) at line 0
  File "helloProcessing.py", line 14
	    if __name__ == &#8216;__main__&#8217;:
	                   ^
SyntaxError: Lexical error at line 14, column 20.  Encountered: "\u00e2" (226), after : ""


```

Can anyone tell me what this error message means ?

---

### Post by wannjanjic on 2009-05-25
Try to change:
```
if __name__ == &#8217;__main__&#8217;:
```
to:
```
if __name__ == "__main__":
```
cause I think that this single quotes **(&#8217;)** in your code aren't the right one **(')**. Probably you've copied this code somewhere from the web ;)

---

### Post by Endolith on 2009-06-16
I got it working once but then I installed Jaunty and today I installed Jython 2.5.0, and I have to figure it all out again.

[http://processing.org/discourse/yabb2/YaBB.pl?num=1212422307](http://processing.org/discourse/yabb2/YaBB.pl?num=1212422307)
My solution for Intrepid: [http://gist.github.com/116485](http://gist.github.com/116485)
[http://processing.org/discourse/yabb2/YaBB.pl?num=1220794099](http://processing.org/discourse/yabb2/YaBB.pl?num=1220794099)
[http://processing.org/discourse/yabb2/YaBB.pl?num=1206614956](http://processing.org/discourse/yabb2/YaBB.pl?num=1206614956)
Other links:  [http://processing.org/hacks/hacks:livecoding#python-jython](http://processing.org/hacks/hacks:livecoding#python-jython)

Ideally, I'd like a wrapper so I can make sketches as simply as this.  Is it possible?

[php]from jyprocessing import *

def setup():
    size(800, 800)
    colorMode(RGB, 100)
    stroke(100)
    strokeWeight(15)
    smooth()

def draw():
    background(192, 64, 0)
    line(150, 25, mouseX, mouseY)

[/php]

---

