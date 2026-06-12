---
title: "Copying Wireless Drivers"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by bnshrdr on 2009-05-01
I know this sounds insane (well maybe not) but I have an HP Pavilion dv6000 laptop that originally shipped with Windows Vista, which I have long since thrown away.  I currently run Jaunty/Windows XP.  Problem is, I have never been able to get the wireless drivers working in XP, but they work right out of the box in Jaunty.  I know this is no big surprise for many of you, but is there any way I can harvest the driver and put it to use on my XP partition?

I don't have any HP support because it came with Vista, not XP, crappy right?

If you guys have any good suggestions, I'm all ears.  Thanks!

---

### Post by 67GTA on 2009-05-01
If it is a native Linux driver, it will not work with Windows. They are not compatible. What wireless card do you have? Post the output of ```
lspci 
```from a terminal.

---

### Post by bnshrdr on 2009-05-01
Here is the output
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by 67GTA on 2009-05-01
You could download the driver in Linux, and then transfer it to your Windows partition to install when your booted in to Windows. Have you tried here? It is supposed to be for your card. [http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2259](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2259)

---

### Post by bnshrdr on 2009-05-01
Haha, thanks!

Last time I download drivers off of HP's website!

Works great.

---

### Post by 67GTA on 2009-05-01
Those are updated drivers straight from Intel. Usually the PC vendors drivers are out of date. It is better to go straight to the source:)

---

