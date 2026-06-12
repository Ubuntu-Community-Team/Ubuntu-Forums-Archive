---
title: "Blender, Ubuntu 7.10 64 and Python 2.5"
date: 2008-04-13
forum: Multimedia Production
---

### Post by oblio9 on 2008-04-13
Hopefully this is the right place for this. I am running Ubuntu 7.10 64-bit. Python 2.5 is installed. I downloaded blender 2.46 from Blender.org for python 2.5. I saved it to a folder in my home directory, untarred it, opened up a terminal and tried to run ./blender from that directory and got the following error:
> ./blender: error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory
I tried moving the folder to the root of my home directory, no dice. I downloaded Blender 2.44 from Synaptic and it runs and finds python 2.5 fine. I did some searching on adding paths in Linux but am not sure that is the correct path. Anyone run into this and know the fix?
Much thanks for your time.

---

### Post by cotcot on 2008-04-13
Do you have in /usr/lib a file with a name that is nearly libpython2.5.so.1.0 ?
(Is the file not present or is blender not able to find it ?)

---

### Post by oblio9 on 2008-04-13
I did find the file there. Just blender 2.45 wont find it. I downloaded 2.46RC1 and that works fine. I guess I'll just work out of that then. Thanks for your help.

---

### Post by cotcot on 2008-04-13
It is worth to go on with 2.46rc1. The video editor has been improved.

---

