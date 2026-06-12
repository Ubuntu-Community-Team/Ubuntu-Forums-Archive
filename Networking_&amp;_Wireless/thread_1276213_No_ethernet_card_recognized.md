---
title: "No ethernet card recognized"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by Flux45 on 2009-09-26
Greetings,
Posted this in Install & Upgrades also.
I recently installed Unbuntu 9.04 on an external hard drive and it seems to not be recognizing my Ethernet card. I have (what windows reports to be) an Intel Pro 1000 PL card that is embedded on a D975BX2 motherboard (intel quad core 975 processor). I have looked at many threads regarding this issue, and was ultimately led to Intel's download website [http://downloadcenter.intel.com/Default.aspx](http://downloadcenter.intel.com/Default.aspx) where they have many linux drivers but none for the Pro 1000 PL. 
Is there something simple I am missing. I am linux semi-noob, first home install, but use it frequently at school. 

my output from lspci is as follows:

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
04:00.0 Multimedia audio controller: Creative Labs SB X-Fi
04:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

my output from ethtool -i eth0 is : cannot get driver information, no such device. 
this is the case for ethx where x is any value. 

someone please help me out with this!! iv spent hours researching for myself but have come up with nothing.

thank you

---

### Post by Flux45 on 2009-09-26
if anyone is interested this thread is now being disscussed @

[http://ubuntuforums.org/showthread.php?t=1276211](http://ubuntuforums.org/showthread.php?t=1276211)

---

