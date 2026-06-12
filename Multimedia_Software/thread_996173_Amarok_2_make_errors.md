---
title: "Amarok 2 make errors"
date: 2008-11-28
forum: Multimedia Software
---

### Post by conradmr on 2008-11-28
Following this example ([http://amarok.kde.org/wiki/Compiling:2.0](http://amarok.kde.org/wiki/Compiling:2.0)) to build amarok 2.0 (which is really 1.98 RC 1).

Getting the following error on sudo make install:

```
amarok-1.98-build$ sudo make install
[  4%] Built target generator
[ 10%] Built target qtscript_core
[ 50%] Built target qtscript_gui
[ 53%] Built target qtscript_network
[ 55%] Built target qtscript_sql
[ 55%] Built target qtscript_uitools
[ 58%] Built target qtscript_xml
[ 63%] Built target amarok_taglib
make[2]: *** No rule to make target `/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so', needed by `lib/libamarokplasma.so.2.0.0'.  Stop.
make[1]: *** [src/context/CMakeFiles/amarokplasma.dir/all] Error 2
make: *** [all] Error 2

```

Ultimate goal was to get amarok 2.0 which has corrected its support for last.fm.

any ideas?

---

### Post by conradmr on 2008-11-29
May have just solved the problem. I stopped trying to find packages that I didn't may not have had installed, then came across this link.

"Bug #299270 in kde4libs (Ubuntu): “Can't build KDE apps due to incorrect cmake file”"
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/299270](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/299270)

There are some core files in the cmake defaults that have incorrect paths. 

I'll paste it here in case that link gets moved.

[INDENT]I'm trying to build the kopete tree from the SVN tree, to do some general kopete development work.

However due to an incorrect dependency in the cmake files from the kdelibs5 package, the build fails:

make[2]: *** No rule to make target `/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so', needed by `lib/libkopete.so.4.1.0'. Stop.

It looks like this dependency is caused by the following lines in /usr/share/kde4/apps/cmake/modules/KDELibsDependenciesInternal.cmake:

SET("solid_LIB_DEPENDS" "general;/usr/lib/libQtCore.so;general;/usr/lib/libQtDBus.so;general;/usr/lib/libQtXml.so;general;/usr/lib/libQtGui.so;general;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

SET("solid_LIB_DEPENDS" "/usr/lib/libQtCore.so;/usr/lib/libQtDBus.so;/usr/lib/libQtXml.so;/usr/lib/libQtGui.so;/build/buildd/kde4libs-4.1.2/obj-i486-linux-gnu/lib/libkdecore.so;")

The reference to the /build/buildd path looks like a left-over from the package build system. These paths should instead reference /usr/lib.

Changing these paths to /usr/lib/libkdecore.so fixes the problem for me.[/INDENT]

---

### Post by rebegin on 2008-11-30
thanks conradmr,

your solution worked, so i was able to compile and run the krusader-svn (Krusader Version 2.0.0-beta2 "Space Odyssey" - with copy queue management!!!!) on my xubuntu 8.10 :D

you made me happy, i was waiting for this for such a long time :D

---

### Post by rebegin on 2008-11-30
hey again, i wrote a quick howto about installing the new beta krusader from source on intrepid. i also quoted your solution, i hope you don't mind...
here's the link:
[http://ubuntuforums.org/showthread.php?t=998552](http://ubuntuforums.org/showthread.php?t=998552)

---

