---
title: "can someone please comfirm for me that this installation worked."
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by peterbug on 2007-04-30
trying to install eyetoy using this guide : [http://ubuntuforums.org/showthread.php?t=272328](http://ubuntuforums.org/showthread.php?t=272328)

my results where :

```

peterbug@peterbug-desktop:~$ tar -xvf /home/peterbug/ov51x-jpeg-1.5.0.tar.gz
ov51x-jpeg-1.5.0/
ov51x-jpeg-1.5.0/test/
ov51x-jpeg-1.5.0/test/Makefile
ov51x-jpeg-1.5.0/test/getjpeg.c
ov51x-jpeg-1.5.0/Makefile
ov51x-jpeg-1.5.0/ov51x-jpeg-core.c
ov51x-jpeg-1.5.0/ov518-decomp.c
ov51x-jpeg-1.5.0/ov51x-jpeg.h
ov51x-jpeg-1.5.0/ov519-decomp.c
ov51x-jpeg-1.5.0/ov511-decomp.c
ov51x-jpeg-1.5.0/ov7670.h
ov51x-jpeg-1.5.0/ChangeLog
peterbug@peterbug-desktop:~$ cd ov51x-jpeg-0.5.4
bash: cd: ov51x-jpeg-0.5.4: No such file or directory
peterbug@peterbug-desktop:~$ cd ov51x-jpeg-1.5.0
peterbug@peterbug-desktop:~/ov51x-jpeg-1.5.0$ sudo make install
Password:
make -C /lib/modules/2.6.20-15-generic/build M=/home/peterbug/ov51x-jpeg-1.5.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg-core.o
/home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg-core.c: In function ‘ov51x_init_isoc’:
/home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg-core.c:5462: warning: assignment from incompatible pointer type
  CC [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov511-decomp.o
  CC [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov518-decomp.o
  CC [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov519-decomp.o
  LD [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg.mod.o
  LD [M]  /home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make -C /lib/modules/2.6.20-15-generic/build M=/home/peterbug/ov51x-jpeg-1.5.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  INSTALL /home/peterbug/ov51x-jpeg-1.5.0/ov51x-jpeg.ko
  DEPMOD  2.6.20-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
peterbug@peterbug-desktop:~/ov51x-jpeg-1.5.0$

```

---

