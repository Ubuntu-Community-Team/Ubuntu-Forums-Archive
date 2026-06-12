---
title: "Network Driver gone AWOL"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2011-11-17
Hi,
After a recent update ran the wired ethernet connection on my PC stopped working (11.10). 

I know that the NIC (onboard controller) is OK because it works when I boot from a live CD (Ubuntu 11.10). 

lspci -nnk | grep -iA2 net
 gives me:

> 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Realtek Semiconductor Co., Ltd. TEG-ECTX Gigabit PCI-E Adapter [Trendnet] [10ec:8168]
03:05.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038]


I'll presume that is r8168 (?)

However, when I modprobe I get 
> 
sudo modprobe r8168
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
FATAL: Module r8168 not found.


I get similar output if I modprobe for r8169, which I am reading others are using for this NIC.

Whatever caused the NIC to stop working after the update is now way beyond me and my head is starting to hurt. 

Can any one help?

Thanks

---

### Post by GuiGuy on 2011-11-18
[http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/](http://www.twm-kd.com/linux/realtek-rtl81688111e-and-ubuntu-linux/)

I followed the instructions from this point forward:
> First you will need the latest driver for your network adapter. Get it here. You will have to extract it and compile it. Current version is 8.025.00.

---

