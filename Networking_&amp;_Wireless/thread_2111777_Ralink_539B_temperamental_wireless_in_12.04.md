---
title: "Ralink 539B temperamental wireless in 12.04"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by +crypto on 2013-02-02
Hello,
My wireless connection is driving me crazy, and I'm not sure how to proceed. At random times, it will just stop connecting to whatever router I've been connected to. The machine still has an IP address, but pages won't load and I can't ping any servers. The wireless icon still says I'm connected. The only way to restore my wireless is to reboot. Then, about once a week or so, the wireless driver just randomly uninstalls itself. The interface, ra0, disappears from ifconfig, and I have to literally "make" and "make install" again (I've saved the driver package locally for just this purpose) and reboot just to have wireless.

The machine is an HP2000 laptop, with a Ralink 539B wireless card. I downloaded the driver package from Ralink, and edited ./os/linux/config.mk to reflect ```
HAS_WPA_SUPPLICANT=y HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y 
```Then I added 
```
 NIC539B_PCIe_DEVICE_ID 0x539B
```everywhere I needed to within ./include/chip/chip_id.h,
./include/chip/rt5390.h,
and ./os/linux/rt_rbus_pci_drv.c

Then I did
```
 sudo make sudo make install sudo modprobe -r rt5390sta sudo modprobe rt5390sta
```and rebooted. Now, once a week or so I have to perform the whole 
make process all over again. What am I doing wrong?

---

### Post by jason0x21 on 2013-07-10
Try installing the backports module mentioned in post #8 of this thread (delete the old module you built, first), it worked for me, and I've got the same setup as you.

[http://ubuntuforums.org/showthread.php?t=2083204](http://ubuntuforums.org/showthread.php?t=2083204)

---

