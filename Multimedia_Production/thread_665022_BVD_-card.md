---
title: "BVD -card"
date: 2008-01-11
forum: Multimedia Production
---

### Post by fabianneke on 2008-01-11
Hello, 
I recently bought a medion akoya (md 96350) with a DVB-T card. 

The back of the dvb-t card mentions the following:

MEDION GFN0401073000L T
type: DVB-T Tuner ExpressCard54
rev: CTX967_V7.2.2
P/N: 40022821
DC Input: +3.3V - 450mA

MEDION AG, 45307 Essen, Germany

I have already searched the internet about installing the driver, but don't seem to find anything about this subject.

Can anybody help me installing this driver?

Some info:
 I'm running ubuntu 7.10

output of lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Multimedia controller: Philips Semiconductors Unknown device 7160 (rev ff)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
08:00.0 Mass storage controller: Silicon Image, Inc. Unknown device 3531 (rev 01)
0a:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

output of lsusb:
```

Bus 001 Device 002: ID 05c8:010b Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c30f Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 08ff:1600 AuthenTec, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. 
Bus 006 Device 001: ID 0000:0000  

```
Thanks in advance,

Fabian

---

### Post by bentob0x on 2008-01-13
Hi Fabian, I have the same laptop and I'm also trying to setup the various pieces of hardware on it.

The 'lspcmcia' command doesn't return anything at all for me for the tv tuner card (even tho the tv tuner card is inserted and the blue light on the side of it is on).

On a different subject, do you get sound on your laptop speakers?

If you're looking for more info on the laptop you can have a look at my post here:
[http://ubuntuforums.org/showthread.php?t=658035]("http://ubuntuforums.org/showthread.php?t=658035")

- bento

PS: if you could change the starting thread to the card reference, it would be better for indexing (DVB-T Tuner ExpressCard54) ;)

---

### Post by fabianneke on 2008-01-13
Hello, 

I do have sound, but not like it should be:
-there is no sound between 0% en 50%, from 50 to 100% it seems to go exponentially (there's a very big difference between 100% en 95% and only a very small difference between 50 and 55%)
-The speakers don't mute when i put in headphones

[size=-2]how can i change the title? [/size]

---

