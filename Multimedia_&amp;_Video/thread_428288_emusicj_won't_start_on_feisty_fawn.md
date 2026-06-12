---
title: "emusicj won't start on feisty fawn"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by water on 2007-04-30
I was using [emusicj]("http://www.kallisti.net.nz/EMusicJ") happily on feisty beta but it will not start after a fresh install to feisty final

When I try to start it from the terminal I get this message 

```
./emusicj: line 50: [: too many arguments
./emusicj: line 52: [: too many arguments
Couldn't find the compiled Java program.

``````
 sudo update-alternatives --config java

```gives : 

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default
[*], or type selection number: 


```Has anybody managed to get [emusicj]("http://www.kallisti.net.nz/EMusicJ") up and running on Feisty?

:water

---

### Post by water on 2007-04-30
I just figured it out, emusicj does not like being in a folder with (a) space(s) in the name.

I have to try and kick the dirty habit of using spaces to make folder names more readable.... ;)

:water

---

