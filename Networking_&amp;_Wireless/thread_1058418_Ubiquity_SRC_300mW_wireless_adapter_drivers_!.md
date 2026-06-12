---
title: "Ubiquity SRC 300mW wireless adapter drivers !"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by ioannou.alexandros on 2009-02-02
**Hi to all,**

I have just installed Ubuntu 8.04. Pretty nice environment. I like it very much. Apart from that I just wondering how I can get my wireless PCMCIA adapter (Ubiquiti) to work without any problems if possible at all.

For those who don't know exactly what type of chipset this card uses...It is based on the Atheros 5004 chipset.

What I want from anyone from you is to kindly give me a little support over my issue..:p

Currently I am using my internal wireless card that my laptop uses which is an Intel Wi-Fi Link 4965/abgn. This worked just fine.

But how about the other one which I mentioned above.

Can someone from you kindly suggest me what I really need to do step-by-step ?

I will much appreciate it if someone can help me!

**THANK YOU VERY MUCH !**

---

### Post by Crafty Kisses on 2009-02-02
What are the results of these commands?
```
lspci
lsusb
```

---

### Post by ioannou.alexandros on 2009-02-02
Hi thanks for the reply I got from you

Hopefully I can get my card to work.

The first command ```
lspci
``` shows

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8700M GT (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:07.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0c:07.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0c:07.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
0c:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


The next command ```
lsusb
``` shows:

Bus 007 Device 002: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 174f:6d51  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 147e:2016  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 006: ID 046d:c052 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by ioannou.alexandros on 2009-02-03
Any one of you guys that can really help me solving my issues?

Thank you

---

