---
title: "Flash"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by bsharp on 2007-11-14
Hey everyone, I was wondering if there is a Linux/GNU replacement for Macromedia Flash.  I don't mean the player, I mean the Flash *creator* program, like GIMP being a replacement for Photoshop.

---

### Post by kshane on 2007-11-14
> **bsharp said:**
> Hey everyone, I was wondering if there is a Linux/GNU replacement for Macromedia Flash.  I don't mean the player, I mean the Flash *creator* program, like GIMP being a replacement for Photoshop.

Have you gone to Macromedia's web site?  They have a number of Linux related things there, I believe...  Don't know off hand if there's any thing for developers/creators.  Been a long time since I've looked around there.

Kevin

---

### Post by bsharp on 2007-11-14
I guess I forgot to mention that part of the reason I was hoping for a GNU equivalent is the hope that I can make .flv files with a free (as in beer) program and not worry whether the copy that I bought from some kid on the corner of my school will land me with a copyright infringement charge.  ( I didn't really buy a pirated version, I was just using it as an example :D)

---

### Post by aysiu on 2007-11-15
F4L?
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by usun on 2007-11-15
you can use Xilisoft FLV converter to have a try. :)

---

### Post by bsharp on 2007-11-15
Thanks, I'll have a try at some of those

---

### Post by bsharp on 2007-11-15
Ok, I downloaded F4L since it seemed like the one closest to what I was looking for, and since it is only available in source right now I have to try to build it myself.  I know virtually nothing about doing this, but I did some research and got the steps to accomplich this.  After extracting the tarball and switching into the f4l-0.2.1 directory, i ran

```
qmake f4l.pro
```

with no errors.  Next, I am supposed to run 

```
make
```

and I get 2 errors from what I can see.  

```
FSDefineSound.h:140: error: extra qualification &#8216;transform::FSDefineSound::&#8217; on member &#8216;FSDefineSound&#8217;
make[1]: *** [FSDefineSound.o] Error 1
make[1]: Leaving directory `/home/brandon/Desktop/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2

```

---

### Post by hoyd on 2008-01-25
ive got the same problem, but found this: [http://ubuntuforums.org/showthread.php?t=69156&highlight=f4l](http://ubuntuforums.org/showthread.php?t=69156&highlight=f4l)

---

