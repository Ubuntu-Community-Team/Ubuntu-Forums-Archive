---
title: "Problems Compiling BPM-DJ 3.6"
date: 2008-08-07
forum: Multimedia Software
---

### Post by timoguin on 2008-08-07
I've downloaded the 3.6 source tarball located at [ftp://bpmdj.yellowcouch.org/bpmdj/](ftp://bpmdj.yellowcouch.org/bpmdj/).

I'm using the defines.debian file for my defines file.  Here are the contents.

```

CPP = g++ -g -O3 -Wall
UIC3 = uic3
RCC = rcc
UIC = uic-qt4
MOC = moc-qt4
CFLAGS += -D COMPILE_OSS -D COMPILE_ALSA -D COMPILE_JACK -D QT_THREAD_SUPPORT -D QT3_SUPPORT
LDFLAGS += -lpthread -lm -lasound -lrt -lfftw3
QT_INCLUDE_PATH = -I/usr/include/qt4/ -I/usr/include/qt4/Qt/
QT_LIBRARY_PATH = 

    (tried blank, as it was
    also tried -I/usr/lib/qt4 -I/usr/lib/qt3
    together and separate)

QT_LIBS = -lQt3Support -lQtGui
BITS = 32

```

I've installed the following dependencies:

libqt4-dev
libqt4-designer
qt4-dev-tools
libfftw3-dev

I can't figure out anything else that needs to be installed.  All the files listed in the defines file are located in a directory that is in the $PATH, mostly in /usr/bin.

However, make fails.  This is the error I get.

```

Compiling:
  [moc] beatgraph-label.moc.cpp
  [moc] renamer.moc.cpp
  [moc] renamer.logic.moc.cpp
  [moc] statistics.moc.cpp
  [moc] cluster-dialog.moc.cpp
  [moc] log-viewer.moc.cpp
  [cpp] beatgraph-label.moc.o
  [cpp] renamer.moc.o
  [cpp] renamer.logic.moc.o
beatgraph-label.moc.cpp: In member function ‘virtual int BeatGraphLabel::qt_metacall(QMetaObject::Call, int, void**)’:
beatgraph-label.moc.cpp:68: error: expected type-specifier before ‘uint8’
beatgraph-label.moc.cpp:68: error: expected `>' before ‘uint8’
beatgraph-label.moc.cpp:68: error: expected `(' before ‘uint8’
beatgraph-label.moc.cpp:68: error: expected primary-expression before ‘)’ token
beatgraph-label.moc.cpp:68: error: ‘uint8’ was not declared in this scope
  [cpp] statistics.moc.o
make[1]: *** [beatgraph-label.moc.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make: *** [.compile] Error 2

```

It appears to be a syntax error or perhaps an incompatibility with the version of my compiler (gcc 4.2.3) or maybe some libraries.  I don't know.

I've been unable to locate hardly any information on this, especially nothing that is Ubuntu specific.

Any help would be greatly appreciated.

---

### Post by timoguin on 2008-08-07
It seems like I've posted this in the wrong forum.  Can a mod please move this thread over to the Multimedia Production forum (or whichever forum is correct).

---

### Post by NatoWelch on 2008-08-26
I had exactly the same problem you describe here with Hardy Heron. Pity there wasn't an answer at the time, but I figured it out. 

Here's a one-line patch for beatgraph-label.h:

```
--- beatgraph-label.h 2008-08-25 23:29:27.000000000 -0700
+++ beatgraph-label.new.h   2008-08-25 23:28:59.000000000 -0700
@@ -26,6 +26,8 @@
 #include <qmutex.h>
 #include "common.h"
 
+typedef unsigned char uint8;
+
 /**
  * The port from Qt3 to Qt4 is a bit tricky here. First: the new painter system does not allow us to draw outside
  * a paintevent message, so we need to fake these. Secondly: the double buffering makes the xor operation effectively

```

I'm no c++ coder; I got lucky on this one. 

For what it's worth, I've been using the binary download from the author's  [download area]("ftp://bpmdj.yellowcouch.org/bpmdj/"). It's the same version. 

I only wanted to compile the source to see if jack was supported. Alas, it isn't (a lot of work for nothing. gah!), but I have discovered that the alsa-jack plugin (from the Debian version of the libasound2-plugins package - The Ubuntu version doesn't have it for some reason) allows bpmdj to talk to jack with no problem. 

Anyway, I hope that helps. bpmdj's beatgraphs and tempo detection are really, really good. Have fun. 

--NAto

---

### Post by timoguin on 2008-08-26
> **NatoWelch said:**
> I had exactly the same problem you describe here with Hardy Heron. Pity there wasn't an answer at the time, but I figured it out. 

Here's a one-line patch for beatgraph-label.h:

I applied that patch, but I get the following error.

```

 [link] bpmdj
/usr/bin/ld: i386 architecture of input file `embedded.a(logo-png.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `embedded.a(bpmdj-ogg.o)' is incompatible with i386:x86-64 output
/usr/bin/ld: i386 architecture of input file `embedded.a(bpmdj-mp3.o)' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status

```

Obviously I'm compiling on a 64 bit system.  I really don't want to do a chroot either.

> **NatoWelch said:**
> For what it's worth, I've been using the binary download from the author's  [download area]("ftp://bpmdj.yellowcouch.org/bpmdj/"). It's the same version.

I tried using the binary, but I get an error on that as well.

```
./bpmdj: error while loading shared libraries: libfftw3.so.3: cannot open shared object file: No such file or directory
```

libfftw3.so.3 is located in /usr/lib, so I'm not sure what the issue is there.

I don't have any preference for using the compiled on the binary version.  I just wanted it to work so I can tag the tempos of all the songs in my music collection.

---

### Post by NatoWelch on 2008-09-06
you'll need to:
# apt-get install libfftw3-3

---

### Post by timoguin on 2008-09-06
> **NatoWelch said:**
> you'll need to:
# apt-get install libfftw3-3

It's installed.  Still doesn't work.

---

### Post by jeremybubs on 2010-08-17
The issue is that it is embedding objects in a 32 bit archive.  The source of the problem is the file "defines", where you see the line

```
BITS = 32

```

Replace that with

```
BITS = 64
```

and it should work

---

