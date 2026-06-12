---
title: "WDA 1320 PCI Wireless Card problem"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by davidovici on 2010-08-31
I am quite new with Ubuntu and I am still learning how things are done.
This is my story: after having a slow and problematic Windows installation I decided to switch to Ubuntu. This is a new install of Ubuntu on a machine that had Windows XP. During installation I got this error: There was an error with the installation, therefore a window console will open. After clicking OK, the installation finished OK. But the wireless card is not recognized. When rebooting there is an error message:  
[   13.466668] ath5k phy0: POST Failed !!!

Below are some more details about the problem. I searched the net but could not find any hints for this specific problem. Any help is welcomed. Thank you.

**1 ) Machine Brand and Model (PC/Laptop)**:
     Code:
     SOYO Desktop AMD64 Athlon 2.6 GHz, 512MB, 80GB  
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     lspci -nn | grep Atheros
00:0b.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01) 
**3 ) check interface:**
     Code:
     $iwconfig
lo        no wireless extensions.

eth0      no wireless extensions. 
**4 ) Check for modules:**
     Code:
     $ lsmod
ath5k                 121792  0 
ath5k                 121792  0 

**5 ) Kernel boot messages**
     Code:
     $dmesg | grep ath
[    0.302404] device-mapper: multipath: version 1.1.0 loaded
[    0.302411] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.460218] ath5k 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.460322] ath5k 0000:00:0b.0: registered as 'phy0'
[   13.466668] ath5k phy0: POST Failed !!!
[   13.489503] ath5k 0000:00:0b.0: PCI INT A disabled
[   13.489543] ath5k: probe of 0000:00:0b.0 failed with error -11 
 **6 ) Network configuration**
     Code:
     $ sudo lshw -C network
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=40 maxlatency=28 mingnt=10
       resources: memory:dffe0000-dffeffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0b:6a:11:49:9e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:d800(size=256) memory:dfffee00-dfffeeff

**7 ) Scan for networks:**
     Code:
     $ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d
Description:    Ubuntu 10.04.1 LTS

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     $ uname -mr
2.6.32-24-generic i686

**10 ) Restarting the network:**
     Code:
     $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                  [ OK ]

---

