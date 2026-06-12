---
title: "Trouble following a how to"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by simonsimon on 2007-01-17
I'm trying to follow [THIS]("http://www.linuxquestions.org/questions/showthread.php?t=503714") and I'm stuck.  A little background info...

I have the intel card that this solution was written for.  

I'm currently troubleshooting loss of sound in Edgy.  Reinstalling alsa, checking sound levels doesn't seem to work.

I'm getting stuck on the following line:

```
sudo ./configure --with-cards=hda-intel --with-sequencer=yes;make;make install 
```

Here's the error message I'm getting (it's at the bottom):

```
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
[COLOR="Red"]checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).[/COLOR]
```

I searched the forums and someone suggested to do this:

```
sudo apt-get install linux-source

```

I did that but still get the error message.  

Can anyone help me with this?

Thanks.  :)

---

### Post by benson444 on 2007-01-17
Check out this thread. Someone with the same error message sorted it by installing linux-headers.

[http://ubuntuforums.org/showthread.php?t=305712](http://ubuntuforums.org/showthread.php?t=305712)

Hope it helps.

---

### Post by majoridiot on 2007-01-17
first, determine your kernel version:

```
uname -r 
```

in this case i got: 2.6.15-27

now, use that info to get your correct source (and grab the kernel header
package, in case you need it:

```
sudo apt-get install linux-source-2.6.15-27 linux-kernel-headers
```

---

### Post by simonsimon on 2007-01-17
Thanks guys.  

I won't be continuing with this particular solution but if it happens again...

:)

---

