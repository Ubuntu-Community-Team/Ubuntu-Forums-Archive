---
title: "I Cant get my wireless network to work please help me"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by theone2215 on 2009-12-12
I have dell inspiron 1501 I just installed Ubuntu 9.10 through Wubi. But I cant get my wireless to work. When I look at the top right icon it says device not ready or something like that this is what I got when I typed in the -C netwrok command:

     *-network               
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:05:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: driver=b43-pci-bridge latency=0
         resources: irq:18 memory:c0200000-c0203fff
    *-network
         description: Ethernet interface
         product: BCM4401-B0 100Base-TX
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:08:00.0
         logical name: eth0
         version: 02
         serial: 00:1c:23:a0:89:ae
         size: 10MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
         resources: irq:21 memory:c0300000-c0301fff
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:1d:d9:0b:ee:d3
         capabilities: ethernet physical wireless
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  

So can anyone help me get my wifi working.

---

### Post by ublintu on 2009-12-12
Hi,

I think you should check this (the second and the third posts can help you) :
[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom)
For the second one you need to have internet and for the third one you need to have CD. Good luck!

---

### Post by t0mppa on 2009-12-12
Like ublintu said, you should use the Broadcom STA driver (that those post help you to install) for BCM4311. The problem with your setup however, is that ssb (shown as b43-pci-bridge) hogs the wireless, because you have a wired interface that uses the b44 driver that depends on it and keeps loading it up even if you blacklist b43.

The workaround for that is to force the system to unload all associated network drivers and then load up the STA (module named wl) first and the wired driver (b44) afterwards. You can accomplish that with:```
sudo modprobe -r b44 b43 ssb wl
sudo modprobe wl
sudo modprobe b44
```

---

