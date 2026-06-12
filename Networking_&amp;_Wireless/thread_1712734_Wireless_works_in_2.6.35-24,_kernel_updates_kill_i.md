---
title: "Wireless works in 2.6.35-24, kernel updates kill it."
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2011-03-23
Hi all,
 
*** UPDATE: This card now fixed in 11.04 kernel. See post #24 here: [http://ubuntuforums.org/showthread.php?p=11133342#post11133342](http://ubuntuforums.org/showthread.php?p=11133342#post11133342)

Strange one. Using 10.10; am an LTS man but couldn't get my new Toshiba Satellite Pro L510 to run on it back in November 2010 whereas 10.10 was fine. Trouble is, everything works in kernel 2.6.35-24 but any kernel update kills the wireless!

Consequently, every time there is a kernel upgrade, I boot up Grub Customiser, untick the new kernel, and boot from the trusty 2.6.35-24. All good. And a bit boring as 10.10 is a rolling release and the kernel updates just keep coming (yawn).

So, here is the vital information:

```
*-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: b4:82:fe:3c:ad:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0019.1207.2010 firmware=63 ip=192.168.0.111 latency=0 multicast=yes wireless=802.11bg
       resources: irq:17 ioport:2000(size=256) memory:d4000000-d4003fff

```I am figuring I am going to need to manually rebuild the driver every time there is a kernel update. I don't remember having to do that when I first got the machine running. Maybe one of the updates (hopefully in the near future) will remedy this problem. 

Any ideas?

---

