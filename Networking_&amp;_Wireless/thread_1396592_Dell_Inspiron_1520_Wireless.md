---
title: "Dell Inspiron 1520 Wireless"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Quicksilvr on 2010-02-02
Hey everyone. I'm new to linux and i'm having problems connecting to a wireless network on my Dell inspiron 1520. i can't seem to enable wireless roaming on ubuntu and i get various error messages when i try. 
When i run iwconfig, i get 
lo        no wireless extensions.
eth0      no wireless extensions. 

lspci gives me
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1) 
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) 
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 

running iwlistscan gives me
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning. 
 

When i right click the network manager, there is no "enable wireless" option. I know that wireless works since i used it last night on windows, and the radio is turned on. If anyone can help me, it would be greatly appreciated.

---

### Post by chili555 on 2010-02-02
> Broadcom Corporation BCM4312 802.11b/g (rev 01) To work correctly, your Broadcom needs firmware. Please see here: [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by superprash2003 on 2010-02-02
have you tried system->admin->hardware drivers?

---

