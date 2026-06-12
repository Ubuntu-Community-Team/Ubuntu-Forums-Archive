---
title: "Wireless not working"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Bofur on 2009-01-12
I just upgraded from 8.04 to 8.10. In 8.04 I used ndiswrapper to install my wireless drivers and they worked wonderful. Now when I install 8.10 my wireless doesn't even work.. I've tried the troubleshooting guide but nothing worked. If I manually go into network connections and add a connection, it doesn't even show up when I click the icon. The drivers are installed because I've tried reinstalling. Here's some outputs that might help figure out the problem.

```
justin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```
```
justin@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:5b:29:e0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5752-v3.19 ip=192.168.1.104 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:9a:e0:41:7f:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I have no idea whats going wrong. It worked fine before now it doesn't. Any ideas would be most helpful!

---

