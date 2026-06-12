---
title: "How do I install/Compile AlsaModular?"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by petal on 2007-05-31
I've been trying to install the Alsa Modular system,:

[http://alsamodular.sourceforge.net/](http://alsamodular.sourceforge.net/)

but I run into trouble when I try to compile the extracted tar. At least I think thats the problem.
When I run the "make" command - it produces and error where Linux is requesting access to g++, which should be installed in the system, but maybe not in the right place?

I'm pretty sure I have all the lib's needed to compile this package, but I'm not sure they are installed in the right place.

Here's the error message I get:

thomas@ubuntu:~/Desktop/ams-1.8.8-rc2$ make
g++ -c -pipe -DLADSPA_PATH="/usr/lib/ladspa:/usr/local/lib/ladspa" -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o canvas.o canvas.cpp
/bin/sh: g++: not found
make: *** [canvas.o] Error 127

Any help would be much appreciated!
Cheers!
Thomas

---

### Post by petal on 2007-06-01
bump

---

