---
title: "ImageMagic --with-gslib wont work"
date: 2011-02-18
forum: Multimedia Software
---

### Post by alienprdkt on 2011-02-18
I have tried numerous ways to try and get ImageMagic to work with ghostscript.

Last I have purged imagemagick install the ghostscript delegate for ghostscript

then reinstalled ImageMagick from source with the option --with-gslib 

but still no luck! Has anyone been able to get ImageMagick to work with ghostscript on Ubuntu?

If so how...

```
 identify -list configure

Path: /usr/local/lib/ImageMagick-6.6.7/config/configure.xml

Name          Value
-------------------------------------------------------------------------------
CC            gcc -std=gnu99 -std=gnu99
CFLAGS        -fopenmp -g -O2 -Wall -pthread
CONFIGURE     ./configure  '--with-gslib'
COPYRIGHT     Copyright (C) 1999-2011 ImageMagick Studio LLC
CPPFLAGS      -I/usr/local/include/ImageMagick
CXX           g++
CXXFLAGS      -g -O2 -pthread
DEFS          -DHAVE_CONFIG_H
DELEGATES     fontconfig freetype jpeg jng png x11 zlib
DISTCHECK_CONFIG_FLAGS --disable-deprecated --with-quantum-depth=16 --with-umem=no --with-autotrace=no --with-fontpath= --with-perl=no
EXEC-PREFIX   /usr/local
FEATURES      OpenMP 
HOST          x86_64-unknown-linux-gnu
LDFLAGS       -L/usr/local/lib 
LIB_VERSION   0x667
LIB_VERSION_NUMBER 6,6,7,7
LIBS          -lMagickCore -lfreetype -ljpeg -lpng -lfontconfig -lX11 -lz -lm -lgomp -lpthread -lltdl
NAME          ImageMagick
PCFLAGS       -fopenmp
PREFIX        /usr/local
QuantumDepth  16
RELEASE_DATE  2011-02-18
VERSION       6.6.7
WEBSITE       http://www.imagemagick.org
```

as you can see 

CONFIGURE ./configure '--with-gslib'

but still no gs in the delegates...

Thanks in advance,

---

