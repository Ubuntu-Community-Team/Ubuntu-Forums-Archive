---
title: "Ubuntu server gspca installation"
date: 2011-10-02
forum: Multimedia Software
---

### Post by Savage_CL on 2011-10-02
I'd like to use the GSPCA webcam driver in conjunction with the "motion" package and my logitech webcam to host a live stream as a sort of security camera, but I cannot seem to get said driver installed. 

I have `gspcav1-20071224.tar.gz' and make.
Untar'd I end up with this:

```
jordan@Armstrong:~/build/gspcav1-20071224$ dir -a
.          cutlog.py    gspca_core.c  Makefile.kld      Sonix         utils
..         decoder      gspca.h       Mars-Semi         Sunplus       Vimicro
changelog  Etoms        license       Pixart            Sunplus-jpeg
Conexant   gspca_build  Makefile      READ_AND_INSTALL  Transvision

```

I ran ./gspca_build, as the READ_AND_INSTALL file specifies, with this result:


```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/jordan/build/gspcav1-20071224 CC=cc modul$
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/jordan/build/gspcav1-20071224/gspca_core.o
/home/jordan/build/gspcav1-20071224/gspca_core.c:37:26: fatal error: linux/config.h: No such $
compilation terminated.
make[2]: *** [/home/jordan/build/gspcav1-20071224/gspca_core.o] Error 1
make[1]: *** [_module_/home/jordan/build/gspcav1-20071224] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [default] Error 2

```

I don't know what else to try. any ideas?

---

### Post by Savage_CL on 2011-10-03
bump

---

