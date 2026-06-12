---
title: "Which driver to use for Wireless card"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by mynameiszanders on 2010-02-19
I seem to be having a problem with my wireless card (amongst other things!) on this brand spanking new laptop of mine. I do not have to switch to Windows again, just because of a few driver issues. And no, being constantly being plugged in with a 2m ethernet cable is not my idea of fun :P

Using the following command, I have the following information for you guys (and gals) out there:

```

mynameiszanders@VIPER:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:20:07:b0:2d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.73 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:19 memory:fe788000-fe788fff ioport:30d0(size=8) memory:fe789c00-fe789cff memory:fe789800-fe78980f

  // I'm guessing this is the important bit?

  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:fe400000-fe403fff


```

Any help would be gratefully appreciated. I know a fair bit about Linux, but nothing about drivers, so please, treat me as a complete novice :P

Thanks, mniz.

EDIT: All other problems have been fixed. Despite the various problems people seem to be having with nVidia and 9.10, the nVidia driver 190.53 worked a treat for me :)

---

