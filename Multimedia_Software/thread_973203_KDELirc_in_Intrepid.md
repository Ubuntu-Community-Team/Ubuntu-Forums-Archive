---
title: "KDELirc in Intrepid"
date: 2008-11-06
forum: Multimedia Software
---

### Post by erikf154 on 2008-11-06
Where did kdelirc go in Intrepid, the package doesn't exist. Found a thread saying it would be in the kdeutils package, but it's not there either...

---

### Post by erikf154 on 2008-11-07
In the the svn in kde i resides in kde/playground/utils/kdelirc, however, there's no playground package for kde in ubuntu. Does nybody know what to do?

---

### Post by dajs on 2008-11-08
not available yet :(

---

### Post by erikf154 on 2008-11-08
I tried to compile it from SVN, but I got an error:

```
# svn co -N svn://anonsvn.kde.org/home/kde/trunk/playground/utils/
# cmakekde
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Found Threads: TRUE
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
CMake Error at /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake:1054 (message):
  Qt compiled without support for -fvisibility=hidden.  This will break
  plugins and linking of some applications.  Please fix your Qt installation.
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindKDE4.cmake:81 (FIND_PACKAGE)
  CMakeLists.txt:3 (find_package)


-- Configuring incomplete, errors occurred!
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by erikf154 on 2008-11-08
> **dajs said:**
> not available yet :(

Anybody knows when?

---

