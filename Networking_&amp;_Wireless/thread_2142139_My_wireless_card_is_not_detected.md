---
title: "My wireless card is not detected"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by hoosierfan24 on 2013-05-04
I am running Ubuntu 13.04 and I can only connect via ethernet my wifi card is not even recognized. I was looking throught the forums and tried to resolve the problem on my own, but couldnt I typed this command

```
lshw - C network
```

and got the following output which leads me to believe it is not detecting the wireless card 

```
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:51:35:1f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.15 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:e400(size=256) memory:bffff400-bffff4ff


```

any help would be greatly appreciated

---

### Post by chili555 on 2013-05-04
Let's dig a bit deeper:```
lspci -nn | grep -e 0200 -e 0280
lsusb
rfkill list all
```

---

### Post by hoosierfan24 on 2013-05-05
output
```
will@will-PW784AA-ABA-M1264N:~$ lspci -nn | grep -e 0200 -e 0280
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
will@will-PW784AA-ABA-M1264N:~$ lsusb
Bus 001 Device 004: ID 0846:9000 NetGear, Inc. WN111(v1) RangeMax Next Wireless [Marvell 88W8362+88W8060]
Bus 001 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 003 Device 006: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
will@will-PW784AA-ABA-M1264N:~$ rfkill list all
will@will-PW784AA-ABA-M1264N:~$ 


```

---

### Post by chili555 on 2013-05-05
Please see here: [http://wikidevi.com/wiki/Netgear_WN111v1](http://wikidevi.com/wiki/Netgear_WN111v1)> ID: 0846:9000...And:> **Linux driver**
noneYour alternative is to get the Windows XP drivers and use ndiswrapper. You seem willing to try to solve problems on your own, but I will be very happy to help if you get stuck.

---

