---
title: "HOW to enable CoverBling applet in amarok &gt;= 2.3.1"
date: 2010-06-09
forum: Multimedia Software
---

### Post by manuw2009 on 2010-06-09
Hi guys,

As some know, the CoverBling applet was introduced in 2.3.1 beta 1, but had to be removed for stability and well, legal issues too (Apple coverflow patent).
If you still want to enjoy it as here :
[http://www.youtube.com/watch?v=LJgYNBXpWGU](http://www.youtube.com/watch?v=LJgYNBXpWGU)
it can be compiled along with amarok, as it was just moved to "playground".
Here we go :
 1. download the amarok sources either through git clone or using 2.3.1 sources
2. cp -rf amarok/playground/context/applets/coverbling amarok/src/context/applets/
3. edit amarok/src/context/applets/CMakeLists.txt and append  "add_subdirectory( coverbling )" to the file to enable the applet compilation
4. follow the regular - understand : "not for beginners" :( amarok git  compilation process ad documented elsewhere (for instance : [http://www.howtoforge.com/how-to-compile-amarok-2-from-git-on-kubuntu-9....]("http://www.howtoforge.com/how-to-compile-amarok-2-from-git-on-kubuntu-9.10-karmic"))
5. Coverbling is now part of the available applets
:guitar:

---

### Post by K.Mandla on 2010-06-13
Moved to Multimedia and Video.

---

