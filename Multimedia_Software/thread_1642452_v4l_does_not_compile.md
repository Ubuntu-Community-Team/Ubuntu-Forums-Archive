---
title: "v4l does not compile"
date: 2010-12-10
forum: Multimedia Software
---

### Post by gbmtoday on 2010-12-10
hey 
I am trying to install v4l on my ubuntu 10.10 and kernel 2.6.35-22 and i get this

```
make -C /home/saeed/dvb/v4l-dvb/v4l 
make[1]: Entering directory `/home/saeed/dvb/v4l-dvb/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.35-22-generic/build
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/saeed/dvb/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.o
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:55: error: 'FIRMWARE_NAME_MAX' undeclared here (not in a function)
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c: In function 'free_firmware':
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:251: error: implicit declaration of function 'kfree'
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c: In function 'load_all_firmwares':
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:313: error: implicit declaration of function 'kzalloc'
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:313: warning: assignment makes pointer from integer without a cast
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:364: warning: assignment makes pointer from integer without a cast
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c: In function 'xc2028_attach':
/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.c:1238: warning: assignment makes pointer from integer without a cast
make[3]: *** [/home/saeed/dvb/v4l-dvb/v4l/tuner-xc2028.o] Error 1
make[2]: *** [_module_/home/saeed/dvb/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/saeed/dvb/v4l-dvb/v4l'
make: *** [all] Error 2

```any suggestions ?

---

### Post by no2498 on 2010-12-11
why not just install it from the package manager

---

### Post by gbmtoday on 2010-12-12
> **no2498 said:**
> why not just install it from the package manager
what's the package name ?! v4l2ucp ?

---

### Post by no2498 on 2010-12-13
v4l-conf

is what i have loaded

---

