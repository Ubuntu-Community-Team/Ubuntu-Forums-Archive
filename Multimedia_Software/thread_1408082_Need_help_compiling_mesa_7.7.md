---
title: "Need help compiling mesa 7.7"
date: 2010-02-15
forum: Multimedia Software
---

### Post by FirebirdTA01 on 2010-02-15
Hi, im building mesa 7.7 linux-cell on ubuntu 9.10 running on a ps3.
I need help as i have run into several errors but this one i can not seem to work around on my own.  When i run make linux-cell it compiles for quite a while but then i get this error:

mklib: Making Linux shared library:  libGLU.so.1.3.070700
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
mklib: Installing libGLU.so.1.3.070700 libGLU.so.1 libGLU.so in ../../../lib
mv: cannot stat `libGLU.so.1.3.070700': No such file or directory
make[5]: *** [../../../lib/libGLU.so] Error 1
make[5]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/glu/sgi'
make[4]: *** [default] Error 1
make[4]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/glu/sgi'
make[3]: *** [default] Error 1
make[3]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src/glu'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/bandit/Projects/Mesa-7.7/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/bandit/Projects/Mesa-7.7'
make: *** [linux-cell] Error 2
root@ubuntu:/home/bandit/Projects/Mesa-7.7# 

please help, im desperate
actually.. i think i found the problem, i was missing libglu1-mesa-dev package so im installing that now,... will post updates here

---

