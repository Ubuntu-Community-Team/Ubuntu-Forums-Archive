---
title: "Sound Juicer Static"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by Count on 2007-05-23
Basically I want to rip all of my cd collection on to my computer. I try to find a cd ripper that will work, and eventually got Sound Juicer to start ripping and encoding, apparently without problems. After ripping some cds, I go to play the files, and all I get is static and some parts of the tracks, this also happens with playback straight from the cds. So far I have only had this problem with Sound Juicer, not sure on the other rippers, and all other audio works without a hitch. If this can't be fixed, I will use another ripper/encoder, but I would rather not.

I am on a Kubuntu 64bit edgy box, and I also manually checked that SJ had all of its dependencies, I will give any other information needed.

---

### Post by stchman on 2007-05-23
> **Count said:**
> Basically I want to rip all of my cd collection on to my computer. I try to find a cd ripper that will work, and eventually got Sound Juicer to start ripping and encoding, apparently without problems. After ripping some cds, I go to play the files, and all I get is static and some parts of the tracks, this also happens with playback straight from the cds. So far I have only had this problem with Sound Juicer, not sure on the other rippers, and all other audio works without a hitch. If this can't be fixed, I will use another ripper/encoder, but I would rather not.

I am on a Kubuntu 64bit edgy box, and I also manually checked that SJ had all of its dependencies, I will give any other information needed.

What are you ripping your CDs to?  MP3, OGG, FLAC?

Let us know.  Ogg is good to go, MP3 requires the proper gstreamer pipeline.  You can get it here on my site:

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

Now I don't know how well this works with x64 distros.

---

### Post by Count on 2007-05-23
I have already done that, which is what bothers me. I've tried mp3, ogg, and flac. Also, I have the same problem when just trying to play from the cd in Sound Juicer.

Technically, I guess the static isn't really static, it's more like the music has been scrambled, closest sound I can think of is a VCR rewinding, except the music is much worse and is running at a normal pace.

---

### Post by Count on 2007-05-23
I tried those packages again and I found that gstreamer0.10-pitfdll couldn't be found. I have the universe and multiverse repos enabled, so I don't know what's going on there. 

According to [http://packages.ubuntu.com/edgy/libs/gstreamer0.10-pitfdll]("http://packages.ubuntu.com/edgy/libs/gstreamer0.10-pitfdll") that package only exists for i386. I downloaded the source code navigated to the directory, ran ./configure, and I got

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking whether to enable maintainer-specific portions of Makefiles... no
configure: configuring pitfdll for development with nano 1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking to see if compiler understands -Wall... yes
checking for ANSI C header files... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GST... configure: error: no GStreamer found
```

I'm not sure what to do from here.

---

### Post by Count on 2007-05-24
:oops: bump

---

### Post by stchman on 2007-05-24
> **Count said:**
> I have already done that, which is what bothers me. I've tried mp3, ogg, and flac. Also, I have the same problem when just trying to play from the cd in Sound Juicer.

Technically, I guess the static isn't really static, it's more like the music has been scrambled, closest sound I can think of is a VCR rewinding, except the music is much worse and is running at a normal pace.

Is it Juicer only?  Juicer uses the plugins that are installed.

---

### Post by Count on 2007-05-24
I've tried Jack, which had an error, and now I'm trying Grip, which after 15 minutes is just showing the ripping 0.02% done, which seems like quite a long time. If/when it gets finished, I'll let you know how the audio is.

---

### Post by Count on 2007-05-24
Grip is still working and I have been working on compiling gstreamer0.10-pitfdll, it configured without a problem after installing some more gstreamer packages, not sure which one fixed it. But now when I run make I get

```
make  all-recursive
make[1]: Entering directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1'
Making all in gst-libs
make[2]: Entering directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs'
Making all in ext
make[3]: Entering directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext'
Making all in loader
make[4]: Entering directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext/loader'
Making all in dmo
make[5]: Entering directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext/loader/dmo'
if /bin/bash ../../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -DNOAVIFILE_HEADERS -I./.. -I./../wine    -g -O2 -MT DMO_AudioDecoder.lo -MD -MP -MF ".deps/DMO_AudioDecoder.Tpo" -c -o DMO_AudioDecoder.lo DMO_AudioDecoder.c; \
        then mv -f ".deps/DMO_AudioDecoder.Tpo" ".deps/DMO_AudioDecoder.Plo"; else rm -f ".deps/DMO_AudioDecoder.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -DNOAVIFILE_HEADERS -I./.. -I./../wine -g -O2 -MT DMO_AudioDecoder.lo -MD -MP -MF .deps/DMO_AudioDecoder.Tpo -c DMO_AudioDecoder.c  -fPIC -DPIC -o .libs/DMO_AudioDecoder.o
In file included from ./../wine/winbase.h:5,
                 from ./../wine/winreg.h:7,
                 from ./../libwin32.h:17,
                 from DMO_AudioDecoder.c:12:
./../wine/winnt.h:625:2: error: #error You need to define a CONTEXT for your CPU
In file included from ./../wine/winbase.h:5,
                 from ./../wine/winreg.h:7,
                 from ./../libwin32.h:17,
                 from DMO_AudioDecoder.c:12:
./../wine/winnt.h:628: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
./../wine/winnt.h:1021: error: expected specifier-qualifier-list before 'PCONTEXT'
./../wine/winnt.h:1034: error: expected declaration specifiers or '...' before 'PCONTEXT'
In file included from ./../wine/winreg.h:7,
                 from ./../libwin32.h:17,
                 from DMO_AudioDecoder.c:12:
./../wine/winbase.h:544: warning: 'packed' attribute ignored for field of type 'CHAR[8]'
In file included from ./../wine/winreg.h:7,
                 from ./../libwin32.h:17,
                 from DMO_AudioDecoder.c:12:
./../wine/winbase.h:1342: error: expected declaration specifiers or '...' before 'CONTEXT'
./../wine/winbase.h:1481: error: expected ';', ',' or ')' before '*' token
In file included from ./../libwin32.h:19,
                 from DMO_AudioDecoder.c:12:
./../wine/com.h:45: warning: '__stdcall__' attribute ignored
./../wine/com.h:46: warning: '__stdcall__' attribute ignored
./../wine/com.h:47: warning: '__stdcall__' attribute ignored
./../wine/com.h:57: warning: '__stdcall__' attribute ignored
./../wine/com.h:58: warning: '__stdcall__' attribute ignored
./../wine/com.h:59: warning: '__stdcall__' attribute ignored
./../wine/com.h:60: warning: '__stdcall__' attribute ignored
In file included from ./../dshow/../wine/module.h:11,
                 from ./../dshow/guids.h:5,
                 from dmo_guids.h:4,
                 from DMO_Filter.h:4,
                 from DMO_AudioDecoder.c:18:
./../dshow/../wine/pe_image.h:60: warning: 'packed' attribute ignored for field of type 'BYTE'
./../dshow/../wine/pe_image.h:62: warning: 'packed' attribute ignored for field of type 'BYTE'
./../dshow/../wine/pe_image.h:64: warning: 'packed' attribute ignored for field of type 'BYTE'
./../dshow/../wine/pe_image.h:66: warning: 'packed' attribute ignored for field of type 'BYTE'
./../dshow/../wine/pe_image.h:67: warning: 'packed' attribute ignored for field of type 'BYTE'
./../dshow/../wine/pe_image.h:69: warning: 'packed' attribute ignored for field of type 'BYTE'
In file included from DMO_Filter.h:5,
                 from DMO_AudioDecoder.c:18:
dmo_interfaces.h:13: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:13: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:13: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:16: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:18: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:21: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:41: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:41: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:41: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:46: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:50: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:62: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:62: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:62: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:65: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:68: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:80: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:80: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:80: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:84: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:87: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:90: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:94: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:98: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:102: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:106: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:109: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:112: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:117: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:121: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:124: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:127: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:128: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:130: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:131: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:132: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:135: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:141: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:146: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:147: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:157: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:157: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:157: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:163: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:165: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:166: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:168: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:178: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:178: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:178: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:184: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:186: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:188: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:200: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:200: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:200: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:203: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:205: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:207: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:217: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:217: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:217: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:221: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:224: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:227: warning: '__stdcall__' attribute ignored
dmo_interfaces.h:230: warning: '__stdcall__' attribute ignored
DMO_AudioDecoder.c:52: warning: '__stdcall__' attribute ignored
make[5]: *** [DMO_AudioDecoder.lo] Error 1
make[5]: Leaving directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext/loader/dmo'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext/loader'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs/ext'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1/gst-libs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pbierman/Desktop/gstreamer0.10-pitfdll_0.9.1.1+cvs20060515.orig/pitfdll-0.9.1.1'
make: *** [all] Error 2
```

Again, not sure what to do from here.

Edit: Grip is having the same problem.

---

