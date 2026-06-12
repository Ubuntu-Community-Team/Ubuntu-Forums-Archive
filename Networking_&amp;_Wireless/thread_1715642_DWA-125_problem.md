---
title: "DWA-125 problem"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by khaj_vah on 2011-03-27
Hello ppl

Recently i have installed ubuntu 10.10 and i have a problem with D-link DWA-125 adapter.I have downloaded a driver from here [http://ftp.dlink.ru/pub/Wireless/DWA-125/Drivers/Linux/](http://ftp.dlink.ru/pub/Wireless/DWA-125/Drivers/Linux/) 
and tried to install as it is written in readme file but after i run a command make i get  this

/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/khajvah/Desktop/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2

can some1 explain me what am i doing wrong??? 
I really need this help me pls ...
I am quite a new user of linux, so pls explain me step-by-step 
(sorry for my english)

---

