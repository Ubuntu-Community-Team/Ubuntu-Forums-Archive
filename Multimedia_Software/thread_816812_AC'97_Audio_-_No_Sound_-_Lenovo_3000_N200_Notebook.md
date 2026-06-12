---
title: "AC'97 Audio - No Sound - Lenovo 3000 N200 Notebook"
date: 2008-06-03
forum: Multimedia Software
---

### Post by sevenworth on 2008-06-03
Hi, I have searched the forums, and am not coming up with a suitable solution.

The sound on the machine (Ubuntu 8.04) appears to be working fine, but I hear nothing. I have unmuted all channels in Alsamixer without any effect.

Output from LSPCI:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)**
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Any help would be appreciated.

---

### Post by pewjumper on 2008-06-18
Mine to same note book no sound also would let my sony cam coder capture

Raw 1394 kernel module not loaded or failure to read/write/dev/raw1394&#8221;


We really need some answers if this is going to expand it is very limited in catching one if only programmers can use it.

I have tried all the ideas. No sound even downloaded drivers from realtek. So for some one who is only familiar with a GUI operating system, what do you do with it how do you install it?

Are these what I need or do I look for another?
[URL="http://http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false[/URL]

---

### Post by Pjotr123 on 2008-06-18
Try this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 6 )

---

### Post by 7.11brown on 2008-06-24
as to the firewire not loading, this worked in the last version.

This is slightly risky, but run kino as root.  I too have the lenovo 3000 n200 ($400 at xmas)

---

