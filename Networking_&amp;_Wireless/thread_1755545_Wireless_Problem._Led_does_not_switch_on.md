---
title: "Wireless Problem. Led does not switch on"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by walnootje on 2011-05-11
Hello,

I am new with Linux and I am trying to figure out how to get my wireless working. Somehow, I can not find the solution. 

My wireless LED does not switch on and it also does not work.

I hope someone can help me out. In some threads I have seen people post some outputs of command from the terminal. I do not know how to copy this because I can not use ctrl + c in the terminal.

Thanks in advance.

---

### Post by DzmitryG on 2011-05-11
To copy from terminal, select text and in text editor (or directly here) click with middle mouse button (or simultaneously left and right buttons if there is no middle one).

```

sudo lshw -C network
rfkill list all

```

---

### Post by chili555 on 2011-05-11
Please run those commands and post them here. You can copy and paste from the terminal as per the attached.

Ctrl+c to copy is from some other operating system. In Linux, it means stop a process running in a terminal. You can try it with:```
ping www.google.com
```It will run continuously, assuming you have an internet connection, until you press Ctrl+c.

---

### Post by walnootje on 2011-05-11
Ok I did the following

rfkill list all
```

yntema@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

sudo lshw -C network 
```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9000000-d9003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:90:1e:20
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:5000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 90:4c:e5:26:25:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

I hope this gives you some more information

---

### Post by DzmitryG on 2011-05-11
Try solution in post 2 of this thread:
[http://ubuntuforums.org/showthread.php?t=1741865](http://ubuntuforums.org/showthread.php?t=1741865)

---

### Post by walnootje on 2011-05-11
I did this and got the following output:
```
Do you want to continue [Y/n]? Y
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Somehow it does not want to install?

---

### Post by DzmitryG on 2011-05-11
Not sure if this will solve it, but did you remove installed driver from "Additional drivers"?

---

