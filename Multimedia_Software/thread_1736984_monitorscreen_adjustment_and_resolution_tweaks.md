---
title: "monitor/screen adjustment and resolution tweaks"
date: 2011-04-22
forum: Multimedia Software
---

### Post by biosphere on 2011-04-22
I'm a linux newbie so please bear with me.  I am running Ubuntu 32bit 10.10.  I have a [dell studio hybrid PC]("http://www.dell.com/us/dfh/p/studio-hybrid/pd") which I am hooking up to my [TCL brand 40" LCD TV]("http://www.amazon.com/L40FHDF11TA-40-Inch-1080p-2-Year-Warranty/dp/B003LPUWWM/ref=sr_1_10?s=tv&ie=UTF8&qid=1303519230&sr=1-10") to use as a media center pc.

The problem I am having is that I can't get the TV's native 1920x1080 resolution to display properly.  The rendered desktop doesn't quite fit in the screen (I think its the top and bottom edges that are cut off) so for example the menu bar at the top is completely off the screen.

1680x1050 works fine in the sense that it fits the full desktop to the screen size, but its not the native res.  In the resolution changer utility, it recognizes that my TV is a TCL brand but mentions 36 in the model name (the TV I have has 40 in the model name to denote 40") so I think Ubuntu is recognizing the wrong size TV.

How can I finagle the screen settings to make the 1920x1080 fit properly on my monitor? Or get Ubuntu to correctly recognize my TV?  My TV is a no-name brand so its hard to find info on it or others setting up linux with it.

Thanks for your help

---

### Post by wolfen69 on 2011-04-22
Post the output of
```
lspci
```

---

### Post by biosphere on 2011-04-22
user@mediacenter:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801H (ICH8 Family) Thermal Reporting Device
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
user@mediacenter:~$

---

### Post by biosphere on 2011-04-24
Anyone have any ideas?  Thanks

---

