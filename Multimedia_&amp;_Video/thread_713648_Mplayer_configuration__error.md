---
title: "Mplayer configuration  error"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by Crash90 on 2008-03-02
Hello everyone,

I am currently trying to install Mplayer on my Ubuntu 7.10 system.  I made sure to use a package handler to ensure that I have all the dependencies. 

When I d/l the source code and try t configure Mplayer to enable gui this is what I have returned.

```
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.1.3, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... GenuineIntel (6:13:8) 
Checking for CPU type ...  Intel(R) Pentium(R) M processor 1.70GHz 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
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
Checking for assembler (as ) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.22-14-generic, ok 
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
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

```

I am stuck. I tried googling, but I have not found very much help (it could be that being tired is not helping either!)

---

### Post by mc4man on 2008-03-03
At the_ very least_ your missing  some build-deps - start with libc6-dev - I'm sure there are more.
Why no support of mmx or sse I don't know
post your configure options

---

### Post by ahaslam on 2008-03-03
Deps:
```
sudo apt-get build-dep mplayer
sudo apt-get install build-essential
```
Suggested configure options:
```
./configure --prefix=/usr --enable-gui --disable-arts --enable-x11 \
      --enable-runtime-cpudetection --confdir=/etc/mplayer --disable-nas \
      --enable-gl --enable-tv-v4l1 --enable-tv-v4l2 --enable-largefiles \
      --disable-liblzo --disable-speex --disable-openal \
      --disable-fribidi --disable-libdv --disable-musepack \
      --language=all --disable-dvdnav --disable-esd --disable-mga \
      --with-extraincdir=/usr/lib/live-media
```
;)

---

### Post by sanddgroper on 2008-03-03
Hi
I know its a stupid question but why not just use synaptic to install mplayer.

Cheers
Sandy

---

### Post by Crash90 on 2008-03-03
> **sanddgroper said:**
> Hi
I know its a stupid question but why not just use synaptic to install mplayer.

Cheers
Sandy

Package - I did dowload the mplayer package and it told me all dependcies were satisfied and then I installed the package. Is that what you are talking about?

If so, then I d/l'd the source and tried this.....Am I doing an extra step?

I am confused - if you use packages do you still need to download tar balls and compile them?


Edit: Had a tard moment. I failed when using synaptic, because I didn't read the instructions completely. THough my question is still valid, if I downloaded the packages off of package.debian.com   and I ran the mplayer package and all depends were met - do I still have to d/l the source and untar/configure/install? If so, why does the package say I have all the depends but when installing the source it tells me I do not?

---

### Post by mc4man on 2008-03-03
> I am confused - if you use packages do you still need to download tar balls and compile them?
NO
> why does the package say I have all the depends but when installing the source it tells me I do not?
 The packages depends are what's needed to install and run app. The source build depends are what's needed for compiling the source to something you can install - you don't 'install' sources
> I failed when using synaptic, because I didn't read the instructions completely
there aren't any instructions - you mark package for installation and then click apply - if it fails you"ll get a message - if you can't figure the cause post error message and someone will square you up 
> I did dowload the mplayer package and it told me all dependcies were satisfied and then I installed the package

then you should have mplayer - ck. applications>sound and video (or open synaptic and search mplayer- see if it's installed)
You should probably for the moment stick to using synaptic to install apps then using external sites

---

### Post by Crash90 on 2008-03-03
Thank you so much!  It's pretty obvious i am very new to Linux/Ubuntu. 

I will check everything out when I get home!

I failed when marking the package - I didn't realize you had to right click. I should probably stop trying to do things at 100 miles per hour at 11:30 at night!

---

### Post by mc4man on 2008-03-03
If you have any issues with the mplayer you installed post back before going willy-nilly
You may want to install smplayer to run your mplayer  (frontend gui) - will make using mplayer much easier to use while your learning
google smplayer for info and some reading

---

