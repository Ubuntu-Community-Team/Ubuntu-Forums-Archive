---
title: "Trying to find linux kernel source on my pc"
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by Gasman on 2005-12-06
I'm trying to compile sound card drivers for my ESS-1869 integrated soundcard on a Compaq Deskpro using info from the ALSA website and the Ubuntu forums.  The first thing I found was that I didn't have a C compiler installed, so I

[COLOR="RoyalBlue"]sudo apt-get install gcc-3.4[/COLOR]

...after which the compile failed (see below)

[COLOR="RoyalBlue"]./configure --with-cards=es1869 --with-sequencer=yes --with-kernel=/sys/kernel;make;make install
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.10
checking cross compile...
checking for directory with kernel source... /sys/kernel
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /sys/kernel/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).[/COLOR]

I've tried to use which to find version.h but have not had any success.  Any ideas for a linux newbie?

-Gasman-

---

### Post by flopsy on 2005-12-06
Do
```

gee@daisy:~$ uname -r
2.6.12-10-686-smp

```

(yours may be different). Take the 2.6.12-10 bit and do
```

gee@daisy:~$ sudo apt-get install linux-headers-2.6.12-10
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.12-10 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

(obviously, I have it installed already).

---

### Post by flopsy on 2005-12-06
And in your ./configure options, you need --with-kernel=/usr, I think.

---

### Post by Gasman on 2005-12-06
Thanks Flopsy :KS , I appreciate the help!

-Gasman-

---

