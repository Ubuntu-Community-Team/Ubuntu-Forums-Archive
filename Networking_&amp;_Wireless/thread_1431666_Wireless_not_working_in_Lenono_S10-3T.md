---
title: "Wireless not working in Lenono S10-3T"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by astrobeaver on 2010-03-16
I just purchased a Lenovo S10-3T and installed Ubuntu 9.10 on it. My ethernet is working but the netbook just would not detect my wireless card. Here are the results of lspci:

tanmay@ceres96U:~$ lspci
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
**07:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)**

Wireless on Windows is working just fine. Apparently, the Lenovo website which has the product information says it has "Network Card: BCM 4313 BGN Wireless" but lspci didn't really show that. Also, installing drivers for BCM 4313 didn't appear to work, but I might be somewhat wrong. 

I appreciate any help!

Thanks!

---

### Post by astrobeaver on 2010-03-16
Note: I followed the instructions on 

[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

but that didn't work either. :(

---

### Post by dav3hit3 on 2010-03-25
Any luck?

I've installed ubuntu 9.10 on several computers and netbooks and (with a wired network connection) got the wireless up and running pretty easy.

Open up the "Synaptic Package Manager"

1st - turn on all repositories for proprietary drivers, etc
2nd - search for "broadcom"
 * install the bcmwl-kernel-source
 * install bcm5700-source
 * install bcmwl-modaliases

These three packages should get you up and running!

---

### Post by astrobeaver on 2010-07-04
It worked after I installed 10.04...

---

