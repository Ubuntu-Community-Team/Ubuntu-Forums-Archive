---
title: "Good connection out of box"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by coryalantaylor on 2009-10-03
I installed a wireless Linksys PCI card, and it worked out of the box. 
I'm on a fresh install of Ubuntu 9.04. I connected to my wireless network fine and started installing updates and stuff. When I restarted I couldn't get internet anymore. 
I could connect to the network, but I couldn't load Google.
I switched over to Windows and worked fine, I switched back still nothing.
I've done several reboots and all I can get is the network, no internet.

Anybody know why?

---

### Post by SoftwareExplorer on 2009-10-04
I don't know why. 
However, those who might know why will probably want to know what you get when you run ```
lspci
```.

---

### Post by coryalantaylor on 2009-10-04
Ok, here is the result of running that code.

```
cory@corydesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:01.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:02.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
05:02.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Device 0015
cory@corydesktop:~$ 



```

Any clues?

---

