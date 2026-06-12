---
title: "Lenovo B575e - WLAN (ubuntu thinks it is Broadcom, but it is Realtek)"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Ninnus on 2013-02-17
Hi,

my boyfriend bought a Lenovo B575e, that came pre-installed with Windows 8. Naturally we replaced it with Ubuntu.

But Ubuntu has decided to use a wrong driver for wireless and I think it sees a wrong device as well.

The laptop has this wireless component physically;
"Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter"
[http://www.ubuntu.com/certification/hardware/201206-11390/components/](http://www.ubuntu.com/certification/hardware/201206-11390/components/)
(It is also on the manufacturers driver page)

But Ubuntu says this;
*-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0100000-f0103fff 

We downloaded the RTL8188CE driver, and built it, but I don't know where to go from here. Somehow it must replace BCM4313?

(Note, in Windows it uses the Realtek driver - and it works - if Windows 8 can be said to be working)

I don't know that much about Linux, only Windows, DOS and z/OS (mainframe programmer here, hi!)

I am sure that we have the RTL8188CE source built correctly, using the correct libraries etc., and it should be in fine shape. What I am unable to figure out, is how to force Ubuntu to use that for the device.

Any advice?

---

### Post by chili555 on 2013-02-17
It may have a Realtek ethernet card, and versions of the B575-series may be available with a Realtek wireless, but it doesn't have a Realtek wireless card. It has a Broadcom. Please run and post:```
lspci -nn | grep -e 0200 -e 0280
```If the Broadcom is what I think it is, it's fairly easy to get going.> z/OS (mainframe programmer here, hi!)Awesome. Can we do all this with machine code? That would be fun. Then let's port Ubuntu to 24-bit!!

---

### Post by Ninnus on 2013-02-17
```

louis@Louis:~$ lspci -nn | grep -e 0200 -e 0280
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

I only write in COBOL & PL/1, not machine code (yet) :-(

---

### Post by chili555 on 2013-02-17
Hook up that ethernet temporarily and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Your wireless should now be humming along.

Time to take up c++ and python!

---

### Post by Ninnus on 2013-02-17
Thanks, that worked perfectly!

I can do C/C++, but I hate Python because when I studied CS my algorithms professor would do algorithms in a tenth of the lines that I did them with in C++. But mine ran faster :-)

---

### Post by chili555 on 2013-02-17
Glad it's working. Please use thread tools at the top to mark Solved.

---

