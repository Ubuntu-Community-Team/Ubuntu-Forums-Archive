---
title: "ucview 0.31 on ubuntu 10.04"
date: 2010-06-09
forum: Multimedia Software
---

### Post by r!ots on 2010-06-09
Hey guys,

I'm trying to install ucview 0.31 on my ubuntu 10.04 system.

When I configure, it stops at this message:

```
checking for UCVIEW... configure: error: Package requirements (libunicapgtk >= 0.2.23 gtk+-2.0 >= 2.8.0 gthread-2.0 >= 2.8.0 gconf-2.0 libucil >= 0.2.2 libglade-2.0 ) were not met:

No package 'gconf-2.0' found

```

I already looked everywhere to find it. Downloading GConf-2.1.90 and compiling didn't work out either. It stops with following message:

```
checking for gmodule-2.0 >= 2.0.1 gobject-2.0 >= 2.0.1 ORBit-2.0 >= 2.4.0 linc >= 0.5.0... Package ORBit-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `ORBit-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'ORBit-2.0' found Package linc was not found in the pkg-config search path. Perhaps you should add the directory containing `linc.pc' to the PKG_CONFIG_PATH environment variable No package 'linc' found
configure: error: Library requirements (gmodule-2.0 >= 2.0.1 gobject-2.0 >= 2.0.1 ORBit-2.0 >= 2.4.0 linc >= 0.5.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

This sounds quite confusing to me, so before messing up my system I'm asking you for help. If you have any advice or solution for my problem, please let me know.

Has anyone succesfully installed ucview on ubuntu 10.04? I desperatly need it to run lasertag, a great software to create 'grafiti' using a laser pointer, a web cam and a projector.

Thx for your help.

---

### Post by r!ots on 2010-06-09
Alright, I found the solution myself: I had to install the libgconf2-dev package. I only searched for gconf-2.0, so I didn't find this package beforehand.

Now I get another error message, when I'm running 'sudo make' (./configure was finished succesfully):

```
~/projects/lasertag/ucview/ucview-0.31$ sudo make
make  all-recursive
make[1]: Entering directory `/home/adrian/projects/lasertag/ucview/ucview-0.31'
Making all in src
make[2]: Entering directory `/home/adrian/projects/lasertag/ucview/ucview-0.31/src'
/usr/bin/gdk-pixbuf-csource --raw --name=icon_ucview_data ../icons/ucview-logo.png > icon-ucview.h
gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I/usr/local/include   -pthread -D_REENTRANT -DORBIT2=1 -I/usr/include/unicap -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -DINSTALL_PREFIX=\""/usr/local"\" -DUCVIEW_DATADIR=\""/usr/local/share/ucview"\" -DUCVIEW_LOCALEDIR=\""/usr/local/share/locale"\" -DUCVIEW_GLADEDIR=\""/usr/local/share/ucview/glade"\" -DUCVIEW_PLUGINDIR=\""/usr/local/lib/ucview/plugins"\" -DUCVIEW_ICONDIR=\""/usr/local/share/ucview/icons"\" -DUCVIEW_GLOBAL_CONFIGDIR=\""/etc/ucview"\" -DUCVIEW_VERSION_STRING=\""0.31"\" -g -O2 -Wall -MT ucview-ucview.o -MD -MP -MF .deps/ucview-ucview.Tpo -c -o ucview-ucview.o `test -f 'ucview.c' || echo './'`ucview.c
In file included from ucview.c:42:
ucview-window.h:15:27: error: ucview/ucview.h: No such file or directory
In file included from ucview.c:42:
ucview-window.h:151: error: expected declaration specifiers or ‘...’ before ‘UCViewSaveImageFileHandler’
make[2]: *** [ucview-ucview.o] Error 1
make[2]: Leaving directory `/home/adrian/projects/lasertag/ucview/ucview-0.31/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adrian/projects/lasertag/ucview/ucview-0.31'
make: *** [all] Error 2

```

Why can't it compile properly? Do you know how to solve this problem?

Thx once again..

---

### Post by r!ots on 2010-06-09
Once again I found the solution myself (thanks to google and [this ucview forum thread]("http://unicap-imaging.org/forums/viewtopic.php?f=8&t=237")). Next time I'm going to search the web properly before asking needless questions.

You have to do the following to compile ucview 0.31:

```

sudo mkdir /usr/include/ucview
cd /to/your/extracted/ucview-0.31
sudo cp ./src/*.h /usr/include/ucview

```

Afterwards make and make install/checkinstall work flawlessly.

According to the ucview-forum thread, it should also be possible to download and compile the latest trunk release from the project's launchpad page using bazaar. The available version contains a fixed makefile, but I wasn't able to configure it using autoconf.

---

