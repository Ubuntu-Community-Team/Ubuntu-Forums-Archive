---
title: "Gigabit Network - Only 4 MB/s"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by CFJ0 on 2009-04-26
I have a gigabit network card in my ASRock G41M-LE and it has been working nice with Ubuntu Server 9.04 64-bit (had no network in 8.10).
The problem is, when the machine is running Windows Server 2008 it transfers at 80MB/s (Harddrive limit) and when its running Ubuntu it only transfers with 5 - 15 MB/s.
I am using Pure-FTPd.

```
root@SERVER:~# lshw -C Network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:19:66:b3:de:5f
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.22 latency=0 link=yes module=r8169 multicast=yes port=MII speed=1GB/s

```

Anyone got some ideas to solve this? :(

---

### Post by CFJ0 on 2009-04-29
When using samba i get the 30MB/s, how come ftp is slower? Im using Pure-FTPd.

---

