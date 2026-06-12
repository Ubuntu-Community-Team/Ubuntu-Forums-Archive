---
title: "Problems compiling mplayer"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Starwindow on 2007-04-20
I'm trying to compile a subversion of mplayer because I was told that it would be able to play back HD DVD .evo files.  Unfortunately it keeps erroring out and I don't know what to do.  Here is log:

```

root ~/mplayer# ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: x86_64
Checking for cc version ... 4.1.2, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... AuthenticAMD (15:35:2) 
Checking for CPU type ...  AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnow ... failed 
It seems that your kernel does not correctly support 3dnow.
To use 3dnow extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnowext ... failed 
It seems that your kernel does not correctly support 3dnowext.
To use 3dnowext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for .align is a power of two ... no 
Checking for awk ... mawk 
Checking for extra headers ... none 
Checking for extra libs ... none 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... no 
Checking for round ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h (see DOCS/HTML/en/faq.html).

```

I'm pretty new to Linux (just started using it a day or so ago) and I'm really stumped.

---

### Post by dvdgorila on 2007-05-20
Did you ever get this to work? Im trying to compile the latest mplayer to play hd-dvds on my htpc. Please advise. if anyone has precompiled subversion mplayer that would be great

---

### Post by dvdgorila on 2007-05-20
guess not

---

### Post by sune_cph on 2007-05-24
Same issue here...anyone knows how to fix this??

---

### Post by thomasio on 2007-06-24
Just install g++ package ;)

---

### Post by zaleb on 2007-09-22
I'm also new to Ubuntu ( <24hrs ) and I started going down this same path.  A much quicker way to get MPlayer installed is to go to Applications -> Add/Remove.  From there you can just check off that you want to install MPlayer - its in the Sound & Video category.  After it finishes go back in to Add/Remove Applications and it then allows you to choose the MPlayer plguin for Mozilla.

---

### Post by shirilover on 2007-09-23
You need the libc6-dev-amd64 and possibly libc6-dev packages to get past that error.
I would compile a deb package, but I am not running x86-64.

Here is a list of packages you will likely need to compile MPlayer:

build-essential
libc6-dev, libncurses5-dev, libesd0-dev, liblircclient-dev, libgtk2.0-dev, libvorbis-dev, libsdl1.2-dev, sharutils, libasound2-dev (>= 1.0.1), liblzo-dev, gawk, libjpeg62-dev, libaudiofile-dev, libsmbclient-dev, libxv-dev, libpng3-dev, libungif4-dev, libcdparanoia0-dev, libxvidcore4-dev, libdv-dev, liblivemedia-dev (>= 2004.05.01), libfreetype6-dev, em8300-headers, libgl1-mesa-dev | libgl-dev, libdvdread-dev, libdts-dev, libtheora-dev, libglu1-mesa-dev | libglu-dev, libartsc0-dev, libfontconfig-dev, libxxf86dga-dev, libxinerama-dev, libxxf86vm-dev, liblame-dev, libxvmc-dev, libggi2-dev, ttf-bitstream-vera, libmpcdec-dev, libspeex-dev, libfribidi-dev, libfaac-dev, sed (>= 4.0), libaa1-dev, libcaca-dev, libx264-dev (>= 1:0.cvs20060720), libpulse-dev, libmad0-dev, ladspa-sdk, libdbus-glib-1-dev

You may also wish to download -> [http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-essential-20061022.zip](http://www1.mplayerhq.hu/MPlayer/releases/codecs/windows-essential-20061022.zip)
and extract the content to either /usr/lib/codecs or /usr/local/lib/codecs

Since you used the --enable-gui switch, you will need to download a skin from [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) and extract its contents to ~/.mplayer/skins

---

### Post by andrew.46 on 2007-09-23
Hi,

 Thanks for the list:

> **shirilover said:**
> 

Here is a list of packages you will likely need to compile MPlayer:

build-essential
libc6-dev, libncurses5-dev, libesd0-dev, liblircclient-dev, libgtk2.0-dev, libvorbis-dev, libsdl1.2-dev, sharutils, libasound2-dev (>= 1.0.1), liblzo-dev, gawk, libjpeg62-dev, [.....[libaa1-dev, libcaca-dev, libx264-dev (>= 1:0.cvs20060720), libpulse-dev, libmad0-dev, ladspa-sdk, libdbus-glib-1-dev



 I have incorporated some of these into my own 'library' of dev files and on re-compiling I have squeezed a little more functionality from mplayer:

[http://people.aapt.net.au/~adjlstrong/ftgws.html](http://people.aapt.net.au/~adjlstrong/ftgws.html)

               Andrew

---

### Post by dvdgorila on 2007-09-25
Have any of you been able to compile mplayer with ea3(Hd-dvd audio) support? there is a post somewhere on doom that explains it but i get an error. At work now so i will post the links when i get home.

---

