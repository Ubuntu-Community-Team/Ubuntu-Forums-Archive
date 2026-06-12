---
title: "Java Apps and OpenGL"
date: 2010-07-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Progressive on 2010-07-11
One of the main reasons why Java apps can be slow and unresponsive is that they are [not compiled using OpenGL]("http://ubuntuforums.org/showthread.php?t=1129187"). I have noticed this problem OpenOffice, Frostwire, and so on... and it definitely seems to be graphics related.

Is there any chance that we could see this changed for Maverick? I know there used to be some push back against OpenGL for legacy hardware. Nowadays even Android phones have OpenGL support. Seems time to move forward.

---

### Post by kahumba on 2010-07-12
Java apps are never compiled with or without OpenGL.
One can tell the Java platform at startup to run a given Java app using a certain rendering backend: xlib, OpenGL (buggy on buggy drivers) or xRender.
The latter (xrender) will be used and enabled by default starting with Java 7 which is expected to be released this Autumn, more info at:
[http://linuxhippy.blogspot.com/2010/06/xrender-pipeline-now-in-jdk7-master.html](http://linuxhippy.blogspot.com/2010/06/xrender-pipeline-now-in-jdk7-master.html)

And yes, telling Java to use OpenGL does speed things up on good video cards with good drivers.
Side note, if you're still using Azureus you should definitely try Transmission, it's orders of magnitude faster and lighter while providing pretty much anything one normally needs and is not packed with tricks to make you watch commercials or sell you anything.

EDIT: but, things like startup time won't be affected in either case so if you're longing for something really light you better use other solutions.

---

### Post by ktp on 2010-07-12
Just to add to this...sun.java2d.opengl=true would only help Java apps using java 2d API.  I don't think the apps mentioned really use java2d anyways.  This, for sure, won't help SWT apps, which for most part, should already be using hardware rendering.

---

