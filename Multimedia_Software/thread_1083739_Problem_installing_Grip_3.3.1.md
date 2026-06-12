---
title: "Problem installing Grip 3.3.1"
date: 2009-03-01
forum: Multimedia Software
---

### Post by missbliss on 2009-03-01
This is what I get when I do the ```
./configure
```

```
sarah@sarah-laptop:~/grip-3.3.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/sarah/grip-3.3.1/missing: Unknown `--run' option
Try `/home/sarah/grip-3.3.1/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking io/cam/cdrom.h usability... no
checking io/cam/cdrom.h presence... no
checking for io/cam/cdrom.h... no
checking sys/mntent.h usability... no
checking sys/mntent.h presence... no
checking for sys/mntent.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking sys/audio.io.h usability... no
checking sys/audio.io.h presence... no
checking for sys/audio.io.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 >= 2.2.0... Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found
configure: error: Library requirements (libgnomeui-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I went in to synaptic and I have lignomeui-0 and libgnomeui-common both 2.24.0 already installed.


Not sure what to do.  Reason I was installing Grip was to have a gui for decoding flac files.

Any help?

---

### Post by Malta paul on 2009-03-01
If you are using Ubuntu 8-10, Gimp ver 2.6.5 is the latest stable release. To install check out:
[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)
:P

---

### Post by missbliss on 2009-03-01
> **Malta paul said:**
> If you are using Ubuntu 8-10, Gimp ver 2.6.5 is the latest stable release. To install check out:
[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)
:P

GRIP not GIMP!!  :P

---

### Post by mc4man on 2009-03-01
Install lignomeui-dev

Edit: is there any difference between the current source and the 3.3.1 in the intrepid repo?
( it appears 3.3.1 was last updated a couple of years ago
> 

Reason I was installing Grip was to have a gui for **decoding** flac files.

you may want to explain that a bit more, while I no longer use use grip, my impression was it was an *audio cd* ripper/encoder

---

### Post by binbash on 2009-03-01
sudo apt-get install libgnomeui-dev

---

### Post by missbliss on 2009-03-01
> **binbash said:**
> sudo apt-get install libgnomeui-dev

I did this and then tried ./configure and got

```
sarah@sarah-laptop:~/grip-3.3.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/sarah/grip-3.3.1/missing: Unknown `--run' option
Try `/home/sarah/grip-3.3.1/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking linux/cdrom.h usability... yes
checking linux/cdrom.h presence... yes
checking for linux/cdrom.h... yes
checking linux/ucdrom.h usability... no
checking linux/ucdrom.h presence... no
checking for linux/ucdrom.h... no
checking sys/cdio.h usability... no
checking sys/cdio.h presence... no
checking for sys/cdio.h... no
checking io/cam/cdrom.h usability... no
checking io/cam/cdrom.h presence... no
checking for io/cam/cdrom.h... no
checking sys/mntent.h usability... no
checking sys/mntent.h presence... no
checking for sys/mntent.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking machine/soundcard.h usability... no
checking machine/soundcard.h presence... no
checking for machine/soundcard.h... no
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/audioio.h usability... no
checking sys/audioio.h presence... no
checking for sys/audioio.h... no
checking sys/audio.io.h usability... no
checking sys/audio.io.h presence... no
checking for sys/audio.io.h... no
checking sun/audioio.h usability... no
checking sun/audioio.h presence... no
checking for sun/audioio.h... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 >= 2.2.0... yes
checking GNOME_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12  
checking GNOME_LIBS... -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgconf-2 -lgthread-2.0 -lrt -lgmodule-2.0 -lgobject-2.0 -lglib-2.0  
checking for vte... Package vte was not found in the pkg-config search path. Perhaps you should add the directory containing `vte.pc' to the PKG_CONFIG_PATH environment variable No package 'vte' found
configure: error: Library requirements (vte) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


```

---

### Post by missbliss on 2009-03-01
> **mc4man said:**
> 


you may want to explain that a bit more, while I no longer use use grip, my impression was it was an *audio cd* ripper/encoder

This is what gave me the notion that it might be useful:

> 

    * Grip is a great ripping and encoding front end and can be easily configured to use flac. See this thread on how to configure Grip for FLAC.

[http://flac.sourceforge.net/download.html](http://flac.sourceforge.net/download.html)

---

### Post by mc4man on 2009-03-01
> Grip is a great ripping and encoding front end
It will work fine to do that (rip and encode to flac), it's just you said "decode"

Your missing (at the very least)
libvte-dev

I really don't think there is any advantage to building grip due to it's age and nothings been 'disabled' in the ubuntu repo version.

If you must, then run this in a terminal (may help to fill in missing build dep's.
```

sudo apt-get build-dep grip
```

Otherwise just
```
sudo apt-get install grip
```

---

### Post by missbliss on 2009-03-01
> **mc4man said:**
> It will work fine to do that (rip and encode to flac), it's just you said "decode"

Oh, crap, I didn't read that carefully.  I guess, I don't need it after all.



On a related note: I found Sound Converter and got it running but it says it's decoding my flac file to mp3 but it doesn't.  It will actually create all the .mp3 files but it takes 2 seconds and they are all 0 bytes.  

??

---

