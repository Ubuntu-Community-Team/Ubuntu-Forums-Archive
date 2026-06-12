---
title: "HP mini 5103 integrated 3G module (WWAN)"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Harri52 on 2011-03-22
Hello,
I have installed Ubuntu 10.10 Desktop i386 edition on HP mini 5103 laptop as multiboot. Windows 7 pro was is the second operating system.

I have not been able to get the integrated 3G module operational within Ubuntu, on W7 it's working correctly.
On W7 I must always switch the module on with HP connection Manager, how to do it with Ubuntu I do not know.

lspci from my HP:

harri@harri-HP-Mini-5103:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
harri@harri-HP-Mini-5103:~$ 

sudo lshw -C network from my HP:

harri@harri-HP-Mini-5103:~$ sudo lshw -C network
[sudo] password for harri: 
  *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:ed:50:84
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.40 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:90200000-90203fff
  *-network
       description: Ethernet interface
       product: 88E8059 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 64:31:50:74:ec:28
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:90100000-90103fff ioport:2000(size=256) memory:90800000-9081ffff


I'm a beginner with Ubuntu, please excuse me if my question is not clearly expressed.

Best Regards

Harri

---

