---
title: "Creative X-Fi XtremeGamer Drivers"
date: 2010-08-19
forum: Multimedia Software
---

### Post by sylosis on 2010-08-19
I have scoured the forums finding different ways to get my sound card working, tried many different things that worked for others but none have worked for me. when i try to install the drivers given by creative i get this on the make command

```
damien@ubuntu:~$ cd ~/Desktop
damien@ubuntu:~/Desktop$ cd XFiDrv_Linux_Public_US_1.00
damien@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.32-24-generic/build M=/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: At top level:
/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:118: fatal error: opening dependency file /home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/.xfi.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/damien/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2
damien@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 

```

any help would be greatly appreciated

---

### Post by sylosis on 2010-08-19
anyone?

---

