---
title: "How to compile mythplugins?"
date: 2008-07-19
forum: Mythbuntu
---

### Post by Dubstar_04 on 2008-07-19
Does anyone know where i can find a tutorial for compiling mythplugins?

I have found this but I can't seem to get it to work:

[http://www.mythtv.org/wiki/index.php/Building_Plugins:HelloMyth](http://www.mythtv.org/wiki/index.php/Building_Plugins:HelloMyth)

I am wanting to compile my own plugins but whatever i try i get:

> sandal@mediabox:~/release-0-21-fixes/mythplugins$ cd mythhello
sandal@mediabox:~/release-0-21-fixes/mythplugins/mythhello$ qmake
sandal@mediabox:~/release-0-21-fixes/mythplugins/mythhello$ make
cd mythhello && make -f Makefile
make[1]: Entering directory `/home/sandal/release-0-21-fixes/mythplugins/mythhello/mythhello'
g++ -c -pipe -Wall -W -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -D_GNU_SOURCE -DPREFIX=\"\" -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_PLUGIN -I/usr/share/qt3/mkspecs/default -I. -I/include -I/include -I/usr/share/qt3/include -o main.o main.cpp
In file included from main.cpp:6:
mythhello.h:4:28: error: mythtv/uitypes.h: No such file or directory
mythhello.h:5:34: error: mythtv/uilistbtntype.h: No such file or directory
mythhello.h:6:29: error: mythtv/xmlparse.h: No such file or directory
mythhello.h:7:32: error: mythtv/mythdialogs.h: No such file or directory
main.cpp:7:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:8:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:9:30: error: mythtv/lcddevice.h: No such file or directory
main.cpp:10:45: error: mythtv/libmythui/myththemedmenu.h: No such file or directory
In file included from main.cpp:6:
mythhello.h:11: error: expected class-name before ‘{’ token
mythhello.h:16: error: expected `)' before ‘*’ token
main.cpp: In function ‘int mythplugin_init(const char*)’:
main.cpp:20: error: ‘gContext’ was not declared in this scope
main.cpp:20: error: ‘MYTH_BINARY_VERSION’ was not declared in this scope
main.cpp: In function ‘int mythplugin_run()’:
main.cpp:28: error: ‘gContext’ was not declared in this scope
main.cpp:31: error: ‘class MythHello’ has no member named ‘exec’
main.cpp: At global scope:
main.cpp:42: error: expected unqualified-id before ‘[’ token
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/sandal/release-0-21-fixes/mythplugins/mythhello/mythhello'
make: *** [sub-mythhello] Error 2
sandal@mediabox:~/release-0-21-fixes/mythplugins/mythhello$ 



I would really appreciate some advice. 

Thanks,

Dubstar_04

---

### Post by Dubstar_04 on 2008-07-20
Someone must know about compiling plugins?

---

### Post by laga on 2008-07-20
Hi,

you probably need to install the libmyth-dev package.

---

### Post by zbenta on 2010-01-05
I also have the same problem and the installation of libmyth-dev didn't solve my problem.

---

