---
title: "trying to play an audio CD with exaile"
date: 2008-08-15
forum: Multimedia Software
---

### Post by Gallo_Pinto on 2008-08-15
exaile tells me

"You need the python-cddb package in order to play audio discs." 

I downloaded CDDB-1.4.tar.gz (I think I got it from sourceforge). It contains what looks like the files I want and a setup.py file. I got this result in my terminal

```
gallo@GALLO:~$ python /home/gallo/temp/CDDB-1.4/setup.py install
running install
running build
running build_py
[COLOR="Red"][U]file CDDB.py (for module CDDB) not found
file DiscID.py (for module DiscID) not found
file CDDB.py (for module CDDB) not found
file DiscID.py (for module DiscID) not found[/U][/COLOR]
running build_ext
building 'cdrom' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c unix/cdrommodule.c -o build/temp.linux-i686-2.5/unix/cdrommodule.o
gcc: unix/cdrommodule.c: No such file or directory
gcc: no input files
error: command 'gcc' failed with exit status 1
gallo@GALLO:~$ 
```

Now those red lines of code there (I've just turned htem red to illustrate), those two files which it double-lists for some reason, are in the same directory as the installer. There is a subfolder called "unix", I tried putting them int here with on luck. If nayoen can help me get pyhton CDDB installed by helping me out here or any other method, I'd greatly appreciate it.

---

### Post by mc4man on 2008-08-15
You can install python-cddb from synaptic.

Otherwise as far as what you were doing you'll need some packages installed, start with build-essential, also in synaptic, and take it from there

---

### Post by Gallo_Pinto on 2008-08-16
Allrighty, that seems to solve that particular problem. I had previously tried from the menu (applications | Add/remove), which did not work, but I couldn't remember what the proper package manager was called.

---

