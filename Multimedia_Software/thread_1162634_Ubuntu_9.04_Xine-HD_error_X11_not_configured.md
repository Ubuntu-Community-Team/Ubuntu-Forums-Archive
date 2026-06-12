---
title: "Ubuntu 9.04 Xine-HD error X11 not configured"
date: 2009-05-17
forum: Multimedia Software
---

### Post by cpufreak2589 on 2009-05-17
I am trying to compile and install Xine-HD for the purposes of tuning in to HD signals with my pcHDTV 5500 card. Upon running sudo ./configure --enable-shared I am presented with an error (after it runs the configure script) that reads:
```
****************************************************************
xine-lib will be installed to /usr/local/lib

This path is not mentioned among the linker search paths in your
/etc/ld.so.conf. This means it is possible that xine-lib will
not be found when you try to compile or run a program using it.
If this happens, you should add /usr/local/lib to
the environment variable LD_LIBRARY_PATH like that:

export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH

Alternatively you can add a line "/usr/local/lib"
to your /etc/ld.so.conf.
****************************************************************


****************************************************************
WARNING! No X11 output plugins will be built.

For some reason, the requirements for building the X11 video
output plugins are not met. That means, that you will NOT be
able to use the resulting xine-lib to watch videos in a window
on any X11-based display (e.g. your desktop).

If this is not what you want, provide the necessary X11 build
dependencies (usually done by installing a package called
XFree86-devel or similar) and run configure again.
****************************************************************

```

I have tried the solution presented in the first asterisked-block that referenced the ld.so.conf file, to no avail. I am a noobie, so I may be missing something stupid.

---

### Post by Chamillo on 2009-11-30
I have the exact same problem! I have spent hours researching this issue to find an answer, but I have not been able to find a solution. The weird thing is that when I installed Xine on my laptop, I didn't have this problem. I don't know why I have this problem with my desktop. Has anyone resolved this issue?

---

### Post by Chamillo on 2010-01-16
After weeks of grief with this issue, I bought a new NVIDIA video card for $30 and all my problems went away. I wish I had known this earlier. It turns out that I had an old video card and it didn't work well with the Linux open source driver.

---

### Post by Yellow Pasque on 2010-01-16
Buying a new video card is unrelated to this error.

The error would be fixed by running configure with --prefix=/usr flag and making sure xorg-dev package was installed (and any other -dev packages necessary to satisfy the program's dependencies).

---

