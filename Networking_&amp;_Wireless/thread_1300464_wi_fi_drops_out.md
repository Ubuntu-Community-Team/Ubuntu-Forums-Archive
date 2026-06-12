---
title: "wi fi drops out"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by jj3502 on 2009-10-25
the wifi on my new gateway lt3105a drops out, asks me for my password and wont connect again. (ubuntu 9.10)

---

### Post by lidex on 2009-10-25
Run this command in terminal and post results:
```
sudo lshw -C network
```

---

### Post by jj3502 on 2009-10-25
now its staying connected but won't allow me to access the internet

```
jeremy@jeremy-laptop:~$ sudo lshw -c network
[sudo] password for jeremy: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:03:0b:f3
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:a000(size=256) memory:cfdef000-cfdeffff(prefetchable) memory:cfdf0000-cfdfffff(prefetchable) memory:cfd00000-cfd0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:61:3b:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.7 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0200000-f020ffff
jeremy@jeremy-laptop:~$ 

```

---

### Post by jj3502 on 2009-10-25
still doesn't work :( :confused:

---

### Post by lidex on 2009-10-25
Nevermind - just realized you're using Karmic



Have you tried Jaunty on this PC?

---

### Post by jj3502 on 2009-10-25
[i cant get anything to install ]("http://ubuntuforums.org/showthread.php?p=8161575")

---

### Post by lidex on 2009-10-25
You upgraded from 9.04 to 9.10?

---

### Post by jj3502 on 2009-10-25
no straight to 9.10, 9,04 didn't work

---

### Post by jj3502 on 2009-10-25
my wifi says its conected but i can't acsses the internet

---

