---
title: "wifi signal not recognised in hardy"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by abhinav.p on 2009-03-20
wireless was working just fine on my dell9300 laptop running hardy until recently,when suddenly it stopped picking signals.i checked the network to ensure it was in roaming mode,which it was.i tried it
below a router just in case it was not getting the signal,still doesnt work!.so finally i assumed the worst that something went wrong so i reinstalled  (clean) hardy from same cd but this time set it to be the only OS on the hard drive.but when i rebooted,it still did not catch the signal(my friend's lap was able to).i checked for the driver,it showed iwp 2200 (in lsmod list).this was the same driver that successfully worked previously.so as a desperate measure,i tried dmesg,the last lines of the output were interesting.they read


 2.798066] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[    2.798071] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    2.798528] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 18
[    2.799449] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    2.931187] ipw2200: Radio Frequency Kill Switch is On:
[    2.931190] Kill switch must be turned off for wireless networking to work.
[    2.282712] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[    2.327257] udev: renamed network interface eth0 to eth1
[    2.363771] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[    2.368789] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.368798] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.368805] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    3.081207] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    3.081236] b44.c:v2.0
[    3.101660] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:e3:42:f7
[    2.524483] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.677634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.748205] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    6.171856] [drm] Loading R300 Microcode




i have no idea what that radio kill switch is!!!it was never an issue when i first worked with the same OS on the same laptop.my laptop does not have an external switch to turn on/off wifi.
so i concluded it has to be set by commands.so how do i do it?

---

### Post by chili555 on 2009-03-20
Please check here and post back if that doesn't do it.

[http://linux.derkeiler.com/Mailing-Lists/SuSE/2007-02/msg01954.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2007-02/msg01954.html)

---

### Post by abhinav.p on 2009-03-22
thanks it helped.its working now..

---

