---
title: "Freeglut3: where are the lib files?"
date: 2012-01-11
forum: Multimedia Software
---

### Post by tomkat3 on 2012-01-11
I posted this [thread]("http://ubuntuforums.org/showthread.php?p=11603139#post11603139") in the General help forum, but now I think it'd be better to ask these questions about nvidia OpenGL libraries here.

I'm trying to make a program called JJVIEWER that uses libraries called glut, glu, and gl (as I noob, I have no idea what they mean).

Here's what's in the make file:
```

CFLAGS          = -O -I$(INCPATH) -I$(SRCPATH) -I/usr/include -I/usr/include/GL -I/usr/local/include -DLINUX
LFLAGS          = -lm -L/usr/lib -L/usr/local/lib -lglut -lglu -lgl -ltiff

```And here's what happens when I 'make' it:

```
gcc -o JJVIEWER object/array.o object/default.o object/display.o object/init.o object/keyboard.o object/main.o object/memory.o object/mouse.o object/read.o object/write.o -lm -L/usr/lib -L/usr/lib/nvidia-current -L/usr/local/lib -lglut -lglu -lgl -ltiff
/usr/bin/ld: cannot find -lglu
/usr/bin/ld: cannot find -lgl
collect2: ld returned 1 exit status
make: *** [JJVIEWER] Error 1

```

---

### Post by tomkat3 on 2012-01-12
Fixed it! For some reason every library I needed was in a different directory! Also, my earlier searches didn't find anything because the file was called libGL instead of libgl, and so forth. Such a hassle...

For posterity, here are the locations of the elusive libraries. I bet every installation puts it someplace different...

lglut ---> /usr/lib
lGL ---> /usr/lib/nvidia-current
libGLU ---> /usr/lib/i386-linux-gnu

I only found libGLU when I put in:

```
$ locate libGLU
```

---

