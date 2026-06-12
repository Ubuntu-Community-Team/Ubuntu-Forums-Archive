---
title: "Not able to compile FAAC"
date: 2008-07-02
forum: Multimedia Software
---

### Post by birdy25 on 2008-07-02
Hi,
 I was not able to make FAAC. I was getting error 

mp4container.cpp: In member function `virtual void MP4Container::Write(MP4File*)
':
mp4container.cpp:210: error: `__STRING' undeclared (first use this function)
mp4container.cpp:210: error: (Each undeclared identifier is reported only once f
or each function it appears in.)
make[3]: *** [mp4container.lo] Error 1
make[3]: Leaving directory `/cygdrive/c/work/AAC/FAAC/faac/common/mp4v2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/cygdrive/c/work/AAC/FAAC/faac/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/cygdrive/c/work/AAC/FAAC/faac'
make: *** [all] Error 2

thanks,

---

### Post by MacP2008 on 2008-07-12
I also have trobule with faac.  When typing ./configure I get this error
config.status: error: cannot find input file: common/mp4v2/Makefile.in.  Help would be great!

---

### Post by xc3RnbFO8P on 2008-07-12
Install **libmp4v2-0** in Synaptic Package Manager
or you can install FAAC in Synaptic.

---

