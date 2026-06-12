---
title: "Could wireless setup be cause of screen freeze?"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by norm.h on 2011-05-11
I'm trying to find out what could be causing intermittent screen freezes.

At the end of March I had a tremendous amount of help from Chilli (I hope he won't mind me mentioning his name) to get my Edimax EW-7711 PCI wireless card working.
The answer was to run the rt2860 driver under ndiswrapper, and all has been OK.

So before I do *anything*, **is it at all possible that my wireless setup could have anything to do with the screen freezes**, which sometimes happen during the boot process, but also other times completely randomly and not associated with any particular event or process?

I can find nothing in any logs, but must admit I'm not sure what I'm looking for:-?:-?

---

### Post by chili555 on 2011-05-11
Let's have a look at:```
lsmod | grep rt2
dmesg | grep -e ndis -e rt2
```I don't mind being called upon at all; I appreciate your confidence.

---

### Post by Ted Zagurski on 2011-05-11
THis is a bump to Norm's issue. I have also been helped in the past by Chili..thanks. I have the same issue when I changed my usb wifi stick to a D-Link DW-125  (It was working 100% with an older D-Link stick, but my kid swiped that one). I will be in the middle of a download, listening to music or watching BBC and there is a screen freeze, and system freeze (no response to key combinations and no HD inuse light). I tried Chili's commands and here is the result

ted@ted-MS-7549:~$ lsmod | grep rt2
ted@ted-MS-7549:~$ dmesg | grep -e ndis -e rt2
[   16.393692] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   16.812548] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[   16.815097] ndiswrapper: driver drt2870 (D-Link Corporation,10/15/2009, 1.04.07.0000) loaded
[   17.620541] wlan0: ethernet device 1c:af:f7:68:c0:71 using NDIS driver: drt2870, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11 Wireless Card.', 07D1:3C16.F.conf
[   17.623928] usbcore: registered new interface driver ndiswrapper
[   17.640412] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
ted@ted-MS-7549:~$ 



Thanks ted

---

### Post by chili555 on 2011-05-11
> I changed my usb wifi stick to a D-Link DW-125 (It was working 100% with an older D-Link stick, but my kid swiped that one).Do you think it's likely that every D-link stick uses the same ndiswrapper driver? I doubt it. Please post:```
lsusb
ndiswrapper -l
```That's a lower-case L there, not a one.

---

### Post by Ted Zagurski on 2011-05-11
After I installed the New D-Link stick I went to the D-Link site and installed the wrapper (under system>administration>windows wireless Drivers) for  the new DW125 stick I used the one under XP. here is the output you requested:

ted@ted-MS-7549:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:3312 Hewlett-Packard OfficeJet J6410
Bus 002 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 07d1:3c16 D-Link System 
Bus 001 Device 004: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ted@ted-MS-7549:~$ ndiswrapper -l
drt2870 : driver installed
    device (07D1:3C16) present (alternate driver: rt2800usb)


thanks ted

---

### Post by chili555 on 2011-05-11
> Bus 001 Device 005: ID [COLOR="Red"]07d1:3c16[/COLOR] D-Link System > $ ndiswrapper -l
drt2870 : driver installed
device (07D1:3C16) present (alternate driver: rt2800usb)By golly, I think it is the same driver! Let's look at:```
lsmod | grep rt2
```

---

### Post by Ted Zagurski on 2011-05-11
Chili result"

ted@ted-MS-7549:~$ lsmod | grep rt2
ted@ted-MS-7549:~$

or nothing?





thanks  ted

---

### Post by chili555 on 2011-05-11
Ted, I think your wireless setup is solid. I suggest you look elsewhere for the cause of lockups.

---

### Post by norm.h on 2011-05-12
> **chili555 said:**
> Let's have a look at:```
lsmod | grep rt2
dmesg | grep -e ndis -e rt2
```I don't mind being called upon at all; I appreciate your confidence.

norm@norm-desktop:~$ lsmod | grep rt2
norm@norm-desktop:~$ 
norm@norm-desktop:~$ dmesg | grep -e ndis -e rt2
[   15.166547] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   15.800782] ndiswrapper: driver rt2860 (Ralink Technology, Corp.,07/06/2010, 3.01.08.0001) loaded
[   15.801320] ndiswrapper 0000:04:02.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.329500] ndiswrapper 0000:04:02.0: setting latency timer to 64
[   16.333485] ndiswrapper: using IRQ 17
[   16.694105] wlan0: ethernet device 00:1f:1f:a5:fe:df using serialized NDIS driver: rt2860, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11 Wireless Card.', 1814:3060.5.conf
[   17.322037] usbcore: registered new interface driver ndiswrapper
norm@norm-desktop:~$ 

Sorry for the delay.

There's more information here:
[http://www.fiftyplusforum.co.uk/forum/index.php/topic,9669.msg272079.html#msg272079](http://www.fiftyplusforum.co.uk/forum/index.php/topic,9669.msg272079.html#msg272079)
and here:
[http://www.sagazone.co.uk/forums/thread/71716/](http://www.sagazone.co.uk/forums/thread/71716/)

---

### Post by MyLinux99 on 2011-05-12
YES!!! Had same issue........looooooong ago. The problem was so bad, had to reinstall OS.

JJ

---

### Post by chili555 on 2011-05-12
@norm.h-

May I see:```
ndiswrapper -l
lsmod | grep -e rt2 -e rt3
```Looks pretty good so far.

---

### Post by norm.h on 2011-05-12
norm@norm-desktop:~$ ndiswrapper -l
rt2860 : driver installed
	device (1814:3060) present (alternate driver: rt2800pci)
norm@norm-desktop:~$ 
norm@norm-desktop:~$ lsmod | grep -e rt2 -e rt3
norm@norm-desktop:~$ 

Boot process froze again this evening, was OK after rebooting with reset button

---

