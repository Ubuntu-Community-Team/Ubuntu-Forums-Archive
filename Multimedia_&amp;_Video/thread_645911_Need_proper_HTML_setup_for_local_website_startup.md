---
title: "Need proper HTML setup for local website startup"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by bliffle on 2007-12-20
I DLed a friends website with ´wget´ and want to set it up as a self contained website on a single computer. In fact, I hope to put it on a DVD so it can simply be run on anotter computer.

Alll the DLed stuff is in a directory called "B¨ on the Desktop and I want to have an icon on the Desktop that will start the website when it&#347; clicked. Everything works once I get to /B/index.html. And I can use a launch command line for the icon  like:

```
firefox file:///home/userid/Desktop/B/index.html

``` 

But, of course, I want to have it independent of browser, OS and userid. So I need the barebones command for starting the website, which I thought would be:

```
B/index.html

```

But I got an error box saying:

```
THERE WAS AN ERROR LAUNCHING THE APPLICATION
Details: Failed to execute child process "B/index.html" (No such file or directory)
```

So I tried setting a File Association in ubuntu (under ¨äll¨) for ¨.html¨ but that didn´t solve it.

Seems to me that in my past Windows use that worked right, that the OS would find the browser by using the ¨.html¨ extension..

Any ideas?

---

### Post by Xiong Chiamiov on 2007-12-21
Well, since you're trying to make it OS-independent, I found [this]("http://research.silmaril.ie/autoruncd/") for you.  Of course, when I tried using htmlview as they suggest, it seems Kubuntu doesn't install it by default, so you'll have to go with [that script]("http://research.silmaril.ie/autoruncd/autorun").  Tell me how it works out.

---

