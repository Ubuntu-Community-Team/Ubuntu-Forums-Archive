---
title: "No wireless network connection ubuntu 8.4"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by morganr on 2009-07-06
I have no experiencne with any form of Linix but Im tiered of windows so I just installed Ubuntu 8.4 of my HP Compaq versario v5000.

The router Im useing is a Belkin 54g and I've got a Broadcom Corp BCM4318.

I have read several Tutorials on how to conect to the net but get stuck on all of them.:confused:

There are no more wiered spaces on the router.

---

### Post by diablo75 on 2009-07-06
> **morganr said:**
> There are no more wiered spaces on the router.

Could you borrow one for a half hour and use it to access the Internet and run System>Administration>Update Manager and install all available updates.  Then restart after they're applied and check to see if you're wireless adapter is working.

Also, I don't have much against 8.04 other than the fact that it's more than a year old, but you *might* want to consider downloading 9.04 and format your hard drive to install that instead.

---

### Post by superprash2003 on 2009-07-06
try this

 connect to a wired connection. and go to system->admin->hardware drivers and try enabling a hardware driver

---

### Post by morganr on 2009-07-06
OK. I've downloaded the driver but now it saying that I need the firmware. Any idea where I can get that.

---

### Post by Sankou on 2009-07-06
I'm using the same adapter in my system. Ubuntu never recognizes it properly... Here's what I did to get it working.

I went to dell's website because many dell laptops use the same chipset and downloaded the wireless driver from there. Then I opened it with the archive manager and extracted the .sys and .inf files. Then I installed ndiswrapper. I used this to install the drivers. That should go very smoothly. Now you need to run this command-

```
lshw -C Network
```

The result should be something like this:

*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 02
       serial: 00:16:01:7d:23:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+usrmaxg** driverversion=1.5

It should say driver=ndiswrapper + [YOURDRIVER]. If it does not, blacklist the driver that's there and run _sudo update-initramfs -k all -u_ and reboot the computer.

---

### Post by morganr on 2009-07-06
All the driver downloads I've found are .exe files and I can't open them in Archive Manager.:mad:

---

### Post by morganr on 2009-07-07
Can anyone post the link

---

### Post by morganr on 2009-07-09
OK. I've done it. I think its right.

But it wireless still isn't connecting.

The results of lshw -C network are:
 
*-network:0            
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:7a:80:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,12/22/2004, 3.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:fb:d1:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.1.1.6 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

