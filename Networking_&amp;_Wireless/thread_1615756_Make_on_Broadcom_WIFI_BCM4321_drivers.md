---
title: "Make on Broadcom WIFI BCM4321 drivers"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by pedrolima88 on 2010-11-07
Hello sirs,
I still try update my broadcom drivers, because when I try use airodump-ng i receive error.
This error:

Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

root@mobile-laptop:/home/mobile/Desktop/wdriver# airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.


I think if I try update my driver cards thats will work fine. 

I dont know why  ubuntu say my chipset is unknown :S and driver is a default?!

Yes, my wifi card is a eth1, this is dafult, i dont change the name.


Then I try update the driver and got this error:

root@mobile-laptop:/home/mobile/Desktop/wdriver# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/mobile/Desktop/wdriver/built-in.o
  CC [M]  /home/mobile/Desktop/wdriver/src/shared/linux_osl.o
  CC [M]  /home/mobile/Desktop/wdriver/src/wl/sys/wl_linux.o
  CC [M]  /home/mobile/Desktop/wdriver/src/wl/sys/wl_iw.o
  LD [M]  /home/mobile/Desktop/wdriver/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/mobile/Desktop/wdriver/wl.o
see include/linux/module.h for more information
  CC      /home/mobile/Desktop/wdriver/wl.mod.o
  LD [M]  /home/mobile/Desktop/wdriver/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
root@mobile-laptop:/home/mobile/Desktop/wdriver# 

I dont know why  receive this error  WARNING: modpost: missing MODULE_LICENSE() in /home/mobile/Desktop/wdriver/wl.o
see include/linux/module.h for more information

anyone can help me please?

Thanks!

---

### Post by chili555 on 2010-11-07
> WARNING: modpost: missing MODULE_LICENSE() in /home/mobile/Desktop/wdriver/wl.oI believe this means that the Broadcom driver is proprietary, not open source. Therefor, the expected GPL license is not present. 

It looks like your 'make' went perfectly well. I'd ignore the warning.

I don't know much about airmon, so I can't answer your other questions.

---

### Post by pedrolima88 on 2010-11-07
Great chili555!
I think the same about my make! Well, I&#314;l continue with the make.
Just for backup driver, where can i find my actual wl driver for backup if dont work ?

Thanks a lot!:guitar:

---

### Post by chili555 on 2010-11-07
It will be installed if you can get a wired ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by pedrolima88 on 2010-11-08
yes i have!

i'll try now:D brb!

---

