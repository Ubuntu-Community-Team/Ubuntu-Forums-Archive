---
title: "Can't build gspca"
date: 2010-02-18
forum: Multimedia Software
---

### Post by debianese on 2010-02-18
I'm trying to install my webcam but with no success so far.

I know there are already a lot of threads about this subject, but none of their solutions worked for me.

every time i run
```
sudo m-a a-i gspca
```
i get the following error

```
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-20-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-20-generic/g ;s/#KVERS#/2.6.31-20-generic/g ; s/_KVERS_/2.6.31-20-generic/g ; s/##KDREV##/2.6.31-20.57/g ; s/#KDREV#/2.6.31-20.57/g ; s/_KDREV_/2.6.31-20.57/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.31-20-generic KERNELDIR=/usr/src/linux-headers-2.6.31-20-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.31-20-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
In file included from /usr/src/modules/gspca/gspca_core.c:845:
/usr/src/modules/gspca/utils/spcausb.h: In function ‘spca5xxRegRead’:
/usr/src/modules/gspca/utils/spcausb.h:95: error: implicit declaration of function ‘info’
/usr/src/modules/gspca/utils/spcausb.h: In function ‘spca_set_interface’:
/usr/src/modules/gspca/utils/spcausb.h:278: error: implicit declaration of function ‘warn’
In file included from /usr/src/modules/gspca/gspca_core.c:853:
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_init’:
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:122: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:136: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:141: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:148: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:176: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h: In function ‘sp5xxfw2_start’:
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:214: error: called object ‘info’ is not a function
/usr/src/modules/gspca/Sunplus-jpeg/sp5xxfw2.h:230: error: called object ‘info’ is not a function
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_ioctl’:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2604: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field ‘type’ specified in initializer
/usr/src/modules/gspca/gspca_core.c:2615: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function ‘video_device_create_file’
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function ‘video_device_remove_file’
/usr/src/modules/gspca/gspca_core.c: In function ‘spca5xx_probe’:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types when assigning to type ‘struct device’ from type ‘struct device *’
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2

```

Can anybody help me?

---

### Post by Mebus on 2010-04-10
I got a similar problem here on Debian Lenny:

[http://paste.pocoo.org/show/199921/](http://paste.pocoo.org/show/199921/)

:confused:

Mebus

---

### Post by someitalian123 on 2010-05-15
I'm having a similar if not the same problem. What do I need to have installed so I can install gspca?

---

### Post by someitalian123 on 2010-05-29
Really no one knows how to fix this, really. I think it's just missing a dependence, could someone just tell me what needs to be installed. I already have the build essentials so it has to be something else.

---

### Post by someitalian123 on 2010-06-10
O.k my solution to this was to install [B]v4l-dvb, gspca is part of it.
[/B]

---

### Post by sbalfour on 2010-06-11
Here's yopur problem: "/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file".  As of Linux kernel version 2.6.26, asm/semaphore.h 
has been deprecated; it is now in /usr/include or <path>/include.  You need to change that #include <asm/semaphore.h> to #include <semaphore.h>.  There may be other instances of the include in other source files, and they will need to be changed, also.  Fundamentally,
you've got a mismatch between your linux headers and application source code.  If you
don't want to change the source, you'll have to back down your kernel level to something 
prior to 2.6.26, so that your headers will work with your application.  I don't actually have
a build environment for your app set up, so I can't work you through this, though I suspect
that there will be a finite cascade of build errors after this one is solved.

                                                                          Stuart

---

