---
title: "No internet..."
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by electrox73 on 2010-09-17
Hi,
I can't connect to my Wi-Fi nor Wired Network, so I have no internet access on my Ubuntu OS, but my Windows Vista connects OK.
And also I have a HP Pavilion DV-7, so I have touch button above the keyboard. One is for enabling/disabling the wireless card*.
Blue = Enabled, Red = Disabled. When I boot Windows Vista, it is blue, and if not, i turn it on by a single tap. But when I boot Ubuntu, it is always red, and can't make it blue, but other touch button work.

*- I am not sure, but it disables the Internet (atleast when I am on Wi-Fi)

---

### Post by DirtDart on 2010-09-17
Please consult the _[Ubuntu Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")_ as it has a flow of several commands to help you determine what to do.

---

### Post by dineshs on 2010-09-17
Can you post the result of```
sudo lshw -C network
```

---

### Post by electrox73 on 2010-09-17
> **dineshs said:**
> Can you post the result of```
sudo lshw -C network
```

OK, here it is:

electrox73@ubuntu:~$ sudo lshw -C network
[sudo] password for electrox73: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:de000000-de003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:80:32:ce
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:3000(size=256) memory:d6010000-d6010fff(prefetchable) memory:d6000000-d600ffff(prefetchable) memory:d6020000-d602ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:21:00:7a:9d:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
electrox73@ubuntu:~$

---

### Post by dineshs on 2010-09-17
I suggest you first try to make the wired part work
For your > product: RTL8111/8168B PCI Express Gigabit Ethernet controllerthe driver loaded is > driver=r8169This may be the issue
try these links
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)
For the wifi part try [this]("http://ubuntuforums.org/showthread.php?t=1307995")

---

