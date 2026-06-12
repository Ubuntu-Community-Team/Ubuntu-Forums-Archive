---
title: "ImageMagick convert SVG &gt; PNG problem"
date: 2010-10-25
forum: Multimedia Software
---

### Post by paulsp on 2010-10-25
[FONT=Arial][SIZE=2][COLOR=#000000]I needed ImageMagick 6.6 on an Ubuntu 10.04 machine, so I compiled 6.6.1-10 from source and have this running on the 10.04 machine. However, when I try to convert a SVG file to PNG, I get this error: ```
$ /usr/local/bin/convert draw11.svg test.png
convert: no decode delegate for this image format `/tmp/magick-XXkWoFuc' @ error/constitute.c/ReadImage/566.
convert: missing an image filename `test.png' @ error/convert.c/ConvertImageCommand/2970.
```When I run convert -list format, I see the following (relevant) entries:


```
SVG  SVG       -w+   Scalable Vector Graphics
```Indicating that there is write support, but no read support for SVG. Could this be the problem? Also, I get this information from convert -list configure:


```
$ convert -list configure


Path: /usr/local/lib/ImageMagick-6.6.1/config/configure.xml


Name          Value
-------------------------------------------------------------------------------
CC            gcc -std=gnu99 -std=gnu99
CFLAGS        -fopenmp -g -O2 -Wall -pthread
CONFIGURE     ./configure 
COPYRIGHT     Copyright (C) 1999-2010 ImageMagick Studio LLC
CPPFLAGS      -I/usr/local/include/ImageMagick
CXX           g++
CXXFLAGS      -g -O2 -pthread
DEFS          -DHAVE_CONFIG_H
DELEGATES     
DISTCHECK_CONFIG_FLAGS --disable-deprecated --with-quantum-depth=16 --with-umem=no --with-autotrace=no --with-fontconfig=no --with-gslib=no --with-fontpath= --with-rsvg=no --with-xml=no --with-perl=no
EXEC-PREFIX   /usr/local
HOST          x86_64-unknown-linux-gnu
LDFLAGS       -L/usr/local/lib 
LIB_VERSION   0x661
LIB_VERSION_NUMBER 6,6,1,10
LIBS          -lMagickCore -lm -lgomp -lpthread 
NAME          ImageMagick
PCFLAGS       -fopenmp
PREFIX        /usr/local
QuantumDepth  16
RELEASE_DATE  2010-10-25
VERSION       6.6.1
WEBSITE       http://www.imagemagick.org


Path: [built-in]


Name          Value
-------------------------------------------------------------------------------
NAME          ImageMagick
```So I have no information whatsoever under DELEGATES. But I am not sure which files and how to install those, if this is the problem. Any help is appreciated.
[/COLOR][/SIZE][/FONT]

---

### Post by augr on 2011-08-14
Doesn't look like you have the xml and rsvg packages installed. You need those to handle svg conversions.

Try installing the appropriate packages to handle the additional formats and then reinstall imagemagick.

first remove imagemagick and current config

next install packages libxml2 librsvg2-bin
(required depends for each package need to be installed and each package might have its own depends so make sure they are all installed or try without first and see if it works - you'll see what's needed in the package tree e.g. [http://packages.ubuntu.com/lucid/graphics/librsvg2-bin](http://packages.ubuntu.com/lucid/graphics/librsvg2-bin) )

then reinstall imagemagick

you should be good to go

---

