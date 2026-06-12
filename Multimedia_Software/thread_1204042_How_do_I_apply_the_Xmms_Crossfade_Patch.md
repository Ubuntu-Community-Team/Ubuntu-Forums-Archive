---
title: "How do I apply the Xmms Crossfade Patch"
date: 2009-07-04
forum: Multimedia Software
---

### Post by TheHorror on 2009-07-04
As the title says, how do I apply the Xmms Crossfade Patch?  I'm using the amd64 OS.  My console shows this:

```

username@MyCPU:~$ patch -p10 < /home/username/.xmms-crossfade-0.3.14/patches/xmms-ALL-1.2.10.patch
missing header for unified diff at line 3 of patch
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- xmms-1.2.10.orig/libxmms/configfile.c      2003-05-19 23:22:07.000000000 +0200
|+++ xmms-1.2.10/libxmms/configfile.c   2006-07-07 12:07:37.000000000 +0200
--------------------------
File to patch: 

```
I read that it's usually supposed to be:  patch -p0 *filename*, but the console tells me the same thing.  I am new to Linux so step-by-step instructions would be nice.  I wonder if the deb file takes care of the bugs the patches fix.  I've done deb-console installation before.  Thanks!

---

### Post by TheHorror on 2009-07-10
Hello?


Anybody there that can help me with this?

---

