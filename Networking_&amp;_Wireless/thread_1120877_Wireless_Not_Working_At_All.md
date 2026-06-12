---
title: "Wireless Not Working At All"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Graeme2804 on 2009-04-09
Hi,

I have 2 partitions on my Dell Inspiron 1525 which came with Ubuntu 8.04, 1 being Ubuntu 8.10 and 1 being Windows XP SP 2.

I was able to use wireless on Ubuntu up until now.  Although recently I haven't been using Ubuntu at all, I have been using Windows due to games.  Now I have booted into Ubuntu and now I can't seem to use my wireless.

On the network manager, when I click it, it doesn't find any wireless networks.

I have my G1 phone connnected to the wireless network and also another computer in the same room connected to the wireless network.  Also, I'm sat right next to it at the moment but with the wire plugged in.

Previous issues with wireless have been when I try to connect to a network, but I can't even seem to get to that stage.

Any suggestions?  Please also ask if I need to provide additional information.

---

### Post by Graeme2804 on 2009-04-09
*bump*

---

### Post by t0mppa on 2009-04-10
Open up a terminal, run```
lspci
``` and you should be able to figure out what wireless chip your card is using (if not, just paste the whole output of the command into this thread). Different chips require different drivers/work arounds, so without knowing what you're packing, can't really offer much help.

---

### Post by Graeme2804 on 2009-04-10
> **t0mppa said:**
> Open up a terminal, run```
lspci
``` and you should be able to figure out what wireless chip your card is using (if not, just paste the whole output of the command into this thread). Different chips require different drivers/work arounds, so without knowing what you're packing, can't really offer much help.


Ok, my lscpi output is - 

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by t0mppa on 2009-04-10
Ok, as you might have figured out, your chip is: Intel Corporation PRO/Wireless 3945ABG. Personally I have no experience in setting it up, but the threads I Googled claimed it should work in Ubuntu 8.10 without having to install any new drivers. This one for instance shows what to do: [http://ubuntuforums.org/showthread.php?t=865880]("http://ubuntuforums.org/showthread.php?t=865880")

If that doesn't work though, try searching for more help yourself or asking help for that chip type specifically on this forum.

---

### Post by Graeme2804 on 2009-04-13
Well I've posted on that thread because the stuff on that thread did nothing to solve my problem.

Any further suggestions?

---

### Post by t0mppa on 2009-04-14
I'm sorry, but since I don't have the same card, I have no better ideas than you on how to get it up and running. Just wanted to show you how to figure out what chip you have, so you have an easier time googling or pleading help through these forums.

---

