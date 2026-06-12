---
title: "Creative Labs X-Fi Titanium"
date: 2010-01-02
forum: Multimedia Software
---

### Post by paulm2008 on 2010-01-02
Good Evening,

I know [sorry] that this has been covered before [many times] but I cannot find the thread [again].  Basically I'm trying to get my PCIe card [X-Fi] sound card to work.  Downloading and attempting to install the creative Linux driver I get the following error.

make -C /lib/modules/2.6.31-16-generic/build M=/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /XFiDrv_Linux_Public_US_1.00/xfi.o
/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2

What makes it worse, I actually have had it working with an older version of ubuntu, but I lost my "how too" crib sheet :-(

Hope you can assist

Thank You

Paul

---

