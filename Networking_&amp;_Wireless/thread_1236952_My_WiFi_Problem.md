---
title: "My WiFi Problem"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by StarCecil on 2009-08-10
Hello everyone! I am new to ubuntu and am very lost but willing to learn. I have windows xp as my main operating system but i am looking to switch to ubuntu. I have just one problem, my wifi card doesnt seem to work/turn on when i boot into ubuntu!  I really do not know how to fix this and any help would be nice! Sorry if i do not understand your advice just try to remember i am NEW! haha thanks everyone.

---

### Post by Iowan on 2009-08-10
Don't feel intimidated, but ask for explanation if suggestions seem unclear or complex. Although the GUI is more comfortable, sometimes the terminal (AKA command-line-interface, CLI for short) is the easiest way to get information.  So open a terminal, enter **lshw -C network** and paste the results here. If you happen to know the manufacturer of your wifi chip (or even PC/laptop model), you might include it. The goal is to help (and you won't stay new for long...)

---

### Post by StarCecil on 2009-08-10
Alright this is what it gave me.




  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:c3:1f:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=10.0.0.4 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:73:aa:7b:a4:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



And I think the Wifi card is a D-link   i do not know the model number

again thanks for your time.

---

### Post by StarCecil on 2009-08-10
Alright I believe this is the product I have

[http://www.dlink.com/products/?pid=308](http://www.dlink.com/products/?pid=308)


**DWL-G510 High Speed 2.4GHz (802.11g) Wireless PCI Adapter **

---

### Post by RedSingularity on 2009-08-10
What does lspci give you?

---

### Post by StarCecil on 2009-08-10
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)
02:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
02:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

---

### Post by RedSingularity on 2009-08-11
That card you have is not yet supported by Linux.  Just for kicks look in System>Admin>Hardware Drivers.  See if you can activate it there.

---

### Post by StarCecil on 2009-08-13
: / alright   i tried that and it didnt work

thank you for your help everyone!
Looks like im back to windows XP  : /   (SAVE ME)

---

### Post by MarcoPau on 2009-09-22
You can simply set it up with ndiswrapper.

---

