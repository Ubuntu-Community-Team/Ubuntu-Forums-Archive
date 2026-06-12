---
title: "Driver won't load for Echo Mona Soundcard"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by Urreality on 2006-10-05
I'm a complete newbee to the Linux world.  A few days after I installed Ubuntu I installed my Echo Mona soundcard into the system.  I had read on the ALSA website that their drivers would support it. 
But after installing it, ALSA could not find any devices. 

First, I reinstalled ALSA using Synaptic... not effect.

Then, I downloaded the source files from ALSA and tried installing them, but in order to load the ALSA driver it requires the build kernel source and I only got this message.
"checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)."
So I searched for a while and found a single copy of it online but then it did the same thing. 
"root@Urreality:/tmp/alsa-driver-1.0.13# ./configure --with-kernel=/tmp/linux-source-2.6.15-2.6.15
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /tmp/alsa-driver-1.0.13
checking cross compile...
checking for directory with kernel source... /tmp/linux-source-2.6.15-2.6.15
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /tmp/linux-source-2.6.15-2.6.15/include/linux/version.h does not exist.Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)." ](*,) 
I'm not sure why my current ALSA doen't have the driver or how I can install/configure it such that it will work.  
I'd greatly appriecate any help.

---

