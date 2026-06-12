---
title: "Wireless DSL Connection - No Internet"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by aditya.phanindra on 2009-05-25
I've got a BSNL broadband dataone connection. On Windows, I can connect to the usual internet wirelessly as well as using a cable. In ubuntu 9.04, I've added a DSL connection in network manager and I'm only able to connect through cable but not through wireless. If I switch on wireless on my laptop I'm connected to my modem router but there's no internet connectivity (It does not recognize any DSL connection). Can anyone help me on this?
I hope I've made my point clear. Although I've seen a lot of posts and threads related to this topic and tried a lot of solutions but nothing seems to work!

---

### Post by RedSingularity on 2009-05-26
Post your "lspci" output.

---

### Post by superprash2003 on 2009-05-26
yes , strange but true, another person in the forums had the same issue , the DSL tab doesnt work with ONLY WIFI.. i dont know if its a bug or not..have you tried this with a previous version of ubuntu?

---

### Post by aditya.phanindra on 2009-05-29
[B]Hi there,
Sorry for the delay. Here's what you asked for.[/B]

phani@phani-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


**Any help? And yes, I've tried ubuntu 8.10 and it doesn't work on that too.**

---

