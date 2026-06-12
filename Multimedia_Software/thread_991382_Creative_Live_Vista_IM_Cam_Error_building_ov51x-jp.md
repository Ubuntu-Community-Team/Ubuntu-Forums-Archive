---
title: "Creative Live Vista IM Cam: Error building ov51x-jpeg-source"
date: 2008-11-23
forum: Multimedia Software
---

### Post by obsaysditto on 2008-11-23
hello,

lsusb reads
```
041e:405f Creative Technology, Ltd 
```

Steps:
```
sudo apt-get install ov51x-jpeg-source module-assistant
sudo module-assistant a-i ov51x-jpeg
 
```

However, i get the following build error

```
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-7-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-7-generic/g ;s/#KVERS#/2.6.27-7-generic/g ; s/_KVERS_/2.6.27-7-generic/g ; s/##KDREV##/2.6.27-7.16/g ; s/#KDREV#/2.6.27-7.16/g ; s/_KDREV_/2.6.27-7.16/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/ov51x-jpeg'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ov51x-jpeg'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-7-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-7-generic/g ;s/#KVERS#/2.6.27-7-generic/g ; s/_KVERS_/2.6.27-7-generic/g ; s/##KDREV##/2.6.27-7.16/g ; s/#KDREV#/2.6.27-7.16/g ; s/_KDREV_/2.6.27-7.16/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
/usr/bin/make -w -f debian/rules clean
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp build-stamp
dh_clean
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: Nothing to be done for `kdist_config'.
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make KERNEL_DIR=/usr/src/linux KDIR=/usr/src/linux KVERS=2.6.27-7-generic
make[2]: Entering directory `/usr/src/modules/ov51x-jpeg'
/usr/bin/make -C /usr/src/linux M=/usr/src/modules/ov51x-jpeg modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:115:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6382: error: implicit declaration of function ‘video_usercopy’
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: At top level:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6637: error: unknown field ‘owner’ specified in initializer
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6637: warning: initialization from incompatible pointer type
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:6639: error: unknown field ‘type’ specified in initializer
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c: In function ‘ov51x_probe’:
/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.c:8368: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/ov51x-jpeg/ov51x-jpeg-core.o] Error 1
make[3]: *** [_module_/usr/src/modules/ov51x-jpeg] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ov51x-jpeg'
make: *** [kdist_build] Error 2
```


any help is appreciated.
thanks.

---

### Post by duffrecords on 2008-12-10
The ov51x-jpeg-source package from the repositories is broken.  Use [this]("http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page") version instead.  It works on Hardy Heron but I haven't managed to make it work on Intrepid Ibex yet.

---

### Post by duffrecords on 2008-12-20
Actually, I take that back; it does work on Hardy Heron.  You just need to check out the latest code from subversion instead of the 1.5.9 tarball.

---

### Post by libra1780 on 2009-07-02
this cam is working with gspca too now, witch is installed since 2.6.27

---

