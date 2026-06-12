---
title: "smartcam - need help with compiling"
date: 2008-12-21
forum: Multimedia Software
---

### Post by oddish2211 on 2008-12-21
i just installed smartcam, a tool for using your mobile phone over bluetooth as a webcam on your pc.
but when i follow [this]("http://www.softratty.com/article/ef0e9da7921076220e4bb872bacff9bc") tutorial i get an error with compiling

the guide says that i need to go into smartcam/src/driver/ (that's in the unzipped directory of smartcam) and then execute this command;
```
make -C /lib/modules/`uname -r`/build M=`pwd` modules
```

but than i get this as an answer

```
make: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/oddish2211/Desktop/smartcam/src/driver/smartcam.o
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c: In function ‘smartcam_mmap’:
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:194: error: implicit declaration of function ‘vmalloc_to_pfn’
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:195: error: implicit declaration of function ‘remap_pfn_range’
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:195: error: ‘PAGE_SHARED’ undeclared (first use in this function)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:195: error: (Each undeclared identifier is reported only once
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:195: error: for each function it appears in.)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c: At top level:
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:559: error: ‘video_ioctl2’ undeclared here (not in a function)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:566: error: unknown field ‘type’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:572: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:572: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:572: error: initializer element is not computable at load time
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:572: error: (near initialization for ‘smartcam_vid.index’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:573: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:573: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:573: error: initializer element is not computable at load time
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:573: error: (near initialization for ‘smartcam_vid.debug’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:574: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:574: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:575: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:575: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:576: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:576: warning: initialization from incompatible pointer type
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:577: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:577: warning: initialization from incompatible pointer type
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:578: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:579: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:579: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:579: error: initializer element is not computable at load time
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:579: error: (near initialization for ‘smartcam_vid.users’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: warning: missing braces around initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: warning: (near initialization for ‘smartcam_vid.lock’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: warning: initialization makes integer from pointer without a cast
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: error: initializer element is not computable at load time
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:580: error: (near initialization for ‘smartcam_vid.lock.count.counter’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:581: error: unknown field ‘vidioc_s_std’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:581: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:581: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:582: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:582: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:582: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:583: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:583: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:583: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:584: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:584: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:584: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:585: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:585: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:585: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:586: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:586: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:586: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:587: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:587: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:587: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:588: error: unknown field ‘vidioc_cropcap’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:588: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:588: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:589: error: unknown field ‘vidioc_g_crop’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:589: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:589: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:590: error: unknown field ‘vidioc_s_crop’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:590: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:590: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:591: error: unknown field ‘vidioc_g_parm’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:591: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:591: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:592: error: unknown field ‘vidioc_s_parm’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:592: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:592: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:593: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:593: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:593: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:594: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:594: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:594: warning: (near initialization for ‘smartcam_vid’)
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:596: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:596: warning: excess elements in struct initializer
/home/oddish2211/Desktop/smartcam/src/driver/smartcam.c:596: warning: (near initialization for ‘smartcam_vid’)
make[1]: *** [/home/oddish2211/Desktop/smartcam/src/driver/smartcam.o] Error 1
make: *** [_module_/home/oddish2211/Desktop/smartcam/src/driver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

```

could anyone help me with compiling the driver? i know almost nothing about compiling except following a guide about compiling something.

---

### Post by xunilevol on 2008-12-21
edit

---

### Post by oddish2211 on 2008-12-22
> **xunilevol said:**
> edit

hmm, helpfull.

can anyone help me?

---

### Post by oddish2211 on 2008-12-24
please?

---

### Post by dimitriz on 2009-02-10
Hello friends

i'm having the same problem! In Ubuntu Hardy i compiled without problems, but in Intrepid i got the same error.

Anyone knows how to help us?

thanks

---

### Post by dimitriz on 2009-02-10
Hello again,

i found one solution!!

in this site [ [http://mrgorefestonlinux.blogspot.com/2008/12/far-funzionare-smartcam-su-ubuntu.html](http://mrgorefestonlinux.blogspot.com/2008/12/far-funzionare-smartcam-su-ubuntu.html) ] posted by "Alessandro Ferrari" have one patch to Ubuntu Intrepid kernel 2.6.27 

Direct link to patch: [http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch](http://launchpadlibrarian.net/19222206/smartcam-linux-2.6.27.1.patch)

next steps is:

# patch -p1 < vostro_file.patch
# sudo gedit /etc/udev/rules.d/40-permissions.rules

and then modify

SUBSYSTEM=="video4linux", GROUP="video"

to

SUBSYSTEM=="video4linux", GROUP="video", MODE="0666"


thanks and sorry for the english

---

