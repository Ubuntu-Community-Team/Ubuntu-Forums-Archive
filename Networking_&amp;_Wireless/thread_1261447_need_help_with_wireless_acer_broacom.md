---
title: "need help with wireless acer broacom"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by jeffsabres on 2009-09-08
alritgh i have ubuntu instaled and it wont reconise my wirelesscard

internet work fine in windows xp but not when i boot in ubuntu

also the internet work for my other laptop when im on ubuntu

it work all fine


but on my acer laptop with a broadcom 440x 10/100 wireless card it doesnt

reconise my wireless card

i tried atleast ten diferant tutorial on how to make it work

and still wont work

can someone help me im so disasperate i just cant get it to work

---

### Post by SoftwareExplorer on 2009-09-08
> **jeffsabres said:**
> alritgh i have ubuntu instaled and it wont reconise my wirelesscard

internet work fine in windows xp but not when i boot in ubuntu

also the internet work for my other laptop when im on ubuntu

it work all fine


but on my acer laptop with a broadcom 440x 10/100 wireless card it doesnt

reconise my wireless card

i tried atleast ten diferant tutorial on how to make it work

and still wont work

can someone help me im so disasperate i just cant get it to work
What have you tried sofar?
Also, could you post the output of ```
lspci
``` ?

---

### Post by ductiletoaster on 2009-09-08
Also if you could post which version of Ubuntu you are running...
And i know you said u tried ten different tutorials but did u check out the STICKY at the top of this category?

---

### Post by jeffsabres on 2009-09-08
alright ill post what the result are of that as soon as i can transter them i cant connect to the intenre right now with my laptop

---

### Post by jeffsabres on 2009-09-09
jeff@jeff-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY



that is the result but it was run on my laptop that i can reach the internet on

do i need to run this on the laptop that i cant reach the internet on

---

### Post by jeffsabres on 2009-09-09
heres the result for my acer laptop the one that ubuntu dont reconise my wireless card

jeff@jeff-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
jeff@jeff-laptop:~$ 



also i instaled the wireless driver manger thing instaled the right .inf driver

still dont work

---

### Post by jeffsabres on 2009-09-09
anybody know what i could do

---

### Post by Ayuthia on 2009-09-09
> **jeffsabres said:**
>  INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)


The Broadcom BCM4401 card is your wired card and the Linksys is your wireless one.  You might want to post the results of lspci -nn for your Linksys card or do a search on that card to see what you can find.

EDIT:
You might try this link:
[http://leenooks.com/page/show/Linksys%20%5BAirConn%5D%20INPROCOMM%20IPN%202220%20Wireless%20LAN%20Adapter%20%28rev%2001%29](http://leenooks.com/page/show/Linksys%20%5BAirConn%5D%20INPROCOMM%20IPN%202220%20Wireless%20LAN%20Adapter%20%28rev%2001%29)

It looks like they are using NDISwrapper with a Toshiba L10 104 Windows XP driver from the Toshiba website.  You might check the Acer webiste to see if they have an XP driver for your laptop.

Another link that I found is this one:
[http://phildawson.tumblr.com/post/22267163/how-to-enable-linksys-airconn-inprocomm-ipn-2220](http://phildawson.tumblr.com/post/22267163/how-to-enable-linksys-airconn-inprocomm-ipn-2220)

Hopefully one of them will help.

---

### Post by jeffsabres on 2009-09-10
heres the result jeff@jeff-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:02.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:04.0 Ethernet controller [0200]: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) [17fe:2220]
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:06.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
02:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
jeff@jeff-laptop:~$

---

### Post by jeffsabres on 2009-09-12
ive tried what the tutorial said but still doesnt reconise my card even in network it doesnt

anybody know what i could do

---

