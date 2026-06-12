---
title: "Edimax EW7318 Driver Issue"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by orkinoks on 2009-05-17
Hi,
I am trying to install the driver of EW7318, but I could not make it work anyway.Iwconfig does not see any device named wlan0 or rausb0 even the device is attached. I have tried to install the driver in it's cd but getting the following errors.Can anyone tell me how I can install it on jaunty?There are several guides for previous ubuntu versions but not for jaunty.

ork@ork-desktop:~/Desktop/rt73/Module$ make all
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/ork/Desktop/rt73/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/ork/Desktop/rt73/Module/rtmp_main.o
/home/ork/Desktop/rt73/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/ork/Desktop/rt73/Module/rtmp_main.c:443: error: implicit declaration of function ‘kill_proc’
make[2]: *** [/home/ork/Desktop/rt73/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/ork/Desktop/rt73/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

---

