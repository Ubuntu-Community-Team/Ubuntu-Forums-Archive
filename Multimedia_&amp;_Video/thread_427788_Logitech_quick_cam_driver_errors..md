---
title: "Logitech quick cam driver errors."
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by peterbug on 2007-04-29
hey ok so I'm trying to install a Logitech quick cam driver for linux but I keep getting these errors. can anyone help?

I'm using this guide : [http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)


here is what happens when I try to follow it :

peterbug@peterbug-desktop:~$ tar zxvf /home/peterbug/Desktop/qc-usb-0.6.5.tar.gz
qc-usb-0.6.5/
qc-usb-0.6.5/videodev2.h
qc-usb-0.6.5/qc-vv6410.c
qc-usb-0.6.5/debug.sh
qc-usb-0.6.5/APPLICATIONS
qc-usb-0.6.5/videodevfix.h
qc-usb-0.6.5/README.qce
qc-usb-0.6.5/linux-2.6.8.1-quickcam.patch
qc-usb-0.6.5/linux-2.4.20-quickcam.patch
qc-usb-0.6.5/qc-hdcs.c
qc-usb-0.6.5/qc-pb0100.c
qc-usb-0.6.5/qc-memory.c
qc-usb-0.6.5/freeshm.sh
qc-usb-0.6.5/qc-formats.c
qc-usb-0.6.5/show.c
qc-usb-0.6.5/COPYING
qc-usb-0.6.5/qc-memory.h
qc-usb-0.6.5/testquickcam/
qc-usb-0.6.5/testquickcam/Makefile
qc-usb-0.6.5/testquickcam/testquickcam.h
qc-usb-0.6.5/testquickcam/testquickcam.c
qc-usb-0.6.5/testquickcam/CVS/
qc-usb-0.6.5/CVS/
qc-usb-0.6.5/qc-mjpeg.c
qc-usb-0.6.5/TODO
qc-usb-0.6.5/linux-2.6.7-quickcam.patch
qc-usb-0.6.5/qcweb-info.txt
qc-usb-0.6.5/FAQ
qc-usb-0.6.5/linux-2.6.18.patch
qc-usb-0.6.5/qc-driver.c
qc-usb-0.6.5/quickcam.sh
qc-usb-0.6.5/qcset.c
qc-usb-0.6.5/Modules.symvers
qc-usb-0.6.5/CREDITS
qc-usb-0.6.5/Makefile
qc-usb-0.6.5/quickcam.h
peterbug@peterbug-desktop:~$ cd qc-usb-0.6.5/
peterbug@peterbug-desktop:~/qc-usb-0.6.5$ make all
make -C "/lib/modules/2.6.20-15-generic/build" SUBDIRS="/home/peterbug/qc-usb-0.
6.5" modules V=1 USER_OPT="-DHAVE_UTSRELEASE_H=1"
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are
missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix
 it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/peterbug/qc-usb-0.6.5/.tmp_versions
rm -f /home/peterbug/qc-usb-0.6.5/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/peterbug/qc-usb-0.6.5
  gcc -m32 -Wp,-MD,/home/peterbug/qc-usb-0.6.5/.qc-driver.o.d  -nostdinc -isyste              m /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include inc              lude/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-t              rigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mp              referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulat              e-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-              stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL -DHAV              E_UTSRELEASE_H=1  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc              _driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/peterbug/qc-usb-0              .6.5/.tmp_qc-driver.o /home/peterbug/qc-usb-0.6.5/qc-driver.c
In file included from /home/peterbug/qc-usb-0.6.5/qc-driver.c:47:
/home/peterbug/qc-usb-0.6.5/quickcam.h:79:26: error: linux/config.h: No such fil              e or directory
/home/peterbug/qc-usb-0.6.5/qc-driver.c: In function ‘qc_i2c_init’:
/home/peterbug/qc-usb-0.6.5/qc-driver.c:825: warning: assignment from incompatib              le pointer type
/home/peterbug/qc-usb-0.6.5/qc-driver.c: In function ‘qc_isoc_start’:
/home/peterbug/qc-usb-0.6.5/qc-driver.c:1867: warning: assignment from incompati              ble pointer type
make[2]: *** [/home/peterbug/qc-usb-0.6.5/qc-driver.o] Error 1
make[1]: *** [_module_/home/peterbug/qc-usb-0.6.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [quickcam.ko] Error 2
peterbug@peterbug-desktop:~/qc-usb-0.6.5$

---

### Post by aneeskA on 2008-03-04
hey peterbug,

just try removing this "**linux/config.h**" from the file **qc-usb-0.6.5/quickcam.h**

it would compile smoothly ... it worked for me ... hope it works for you :)

-- anesskA

quote:-

"
In file included from /home/peterbug/qc-usb-0.6.5/qc-driver.c:47:
/home/peterbug/qc-usb-0.6.5/quickcam.h:79:26: error: linux/config.h: No such fil e or directory
"

---

