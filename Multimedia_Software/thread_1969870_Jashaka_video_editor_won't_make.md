---
title: "Jashaka video editor won't make"
date: 2012-04-30
forum: Multimedia Software
---

### Post by wiljago on 2012-04-30
Hey there, I hope this is the right forum for this. If not, I apologize & would be happy to delete this & repost it in the appropriate place.

I'm trying to get Jahshaka running on my laptop, but am running into this problem when I run make and haven't been able to find a fix for it online. Any ideas?

Here's what I get:

cd source/AuxiliaryLibraries/ && make -f Makefile 
make[1]: Entering directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries'
cd blur/ && make -f Makefile 
make[2]: Entering directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/blur'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/blur'
cd FTGL/ && make -f Makefile 
make[2]: Entering directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/FTGL'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/FTGL'
cd particle/ && make -f Makefile 
make[2]: Entering directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/particle'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/particle'
cd apollon/ && make -f Makefile 
make[2]: Entering directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/apollon'
g++ -c -m64 -pipe -g -fPIC -D_REENTRANT -Wall -W -DJAHPREFIX="/usr/local" -D_THREAD_SAFE=true -DJAHTHEMES -DJAHGIFT -DNVIDIA_GPU -DJAHSCRIPT -DJAHLINUX -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I/usr/X11R6/include -I/usr/X11R6/include -I. -o apollonsearchlistview.o apollonsearchlistview.cpp
In file included from /usr/include/qt4/QtCore/qbasicatomic.h:227:0,
                 from /usr/include/qt4/QtCore/qatomic.h:46,
                 from /usr/include/qt4/QtCore/qhash.h:45,
                 from /usr/include/qt4/QtCore/qabstractitemmodel.h:47,
                 from /usr/include/qt4/QtGui/qabstractitemview.h:46,
                 from /usr/include/qt4/QtGui/qlistview.h:45,
                 from apollonlistview.h:21,
                 from apollonsearchlistview.h:21,
                 from apollonsearchlistview.cpp:26:
/usr/include/qt4/QtCore/qatomic_arch.h:92:4: error: #error "Qt has not been ported to this architecture"
In file included from /usr/include/qt4/QtGui/qabstractitemview.h:45:0,
                 from /usr/include/qt4/QtGui/qlistview.h:45,
                 from apollonlistview.h:21,
                 from apollonsearchlistview.h:21,
                 from apollonsearchlistview.cpp:26:
/usr/include/qt4/QtGui/qabstractscrollarea.h:47:1: error: ‘QT_BEGIN_HEADER’ does not name a type
/usr/include/qt4/QtGui/qabstractscrollarea.h:59:40: error: expected initializer before ‘:’ token
make[2]: *** [apollonsearchlistview.o] Error 1
make[2]: Leaving directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries/apollon'
make[1]: ***  Error 2
make[1]: Leaving directory `/home/wiljago/Jashaka/jahshaka/source/AuxiliaryLibraries'
make: ***  Error 2

---

