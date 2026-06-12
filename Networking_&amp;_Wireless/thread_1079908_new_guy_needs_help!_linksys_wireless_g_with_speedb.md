---
title: "new guy needs help!: linksys wireless g with speedbooster wmp54gs"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by blackzmage on 2009-02-24
Hi guys

 I joined the forums a few days ago and I LOVE it! But thats not why i am posting...

I need to know how to install a linksys wireless g with speedbooster (wmp54gs) PCI card for my desktop.
I am currently running ubuntu 8.10 Intrepid Ibex via Wubi. **_I do not have ethernet _**connection so i will have to do this manually. 

EDIT: i have new info, thanks to  chmbrs, i have found out that the chpset is a BCM4318 if that helps.

EDIT2: im trying to connect to a WPA Personal Network

---

### Post by chmbrs on 2009-02-24
what type of chipset is it????????

most wifi cards are detected automatically...

any more info on the card?????????????????????????????/

---

### Post by blackzmage on 2009-02-24
All I know is this

Linksys Wireless G PCI with Speedbooster WMP54GS version 1.4

How do I identfy they chipset?

---

### Post by chmbrs on 2009-02-24
lspci 

in the terminal

---

### Post by blackzmage on 2009-03-01
i typed it in and this is what it gave me (Sorry for not getting the specific info, im really new here ;))

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:09.0 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.1 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.2 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:09.3 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
00:0b.0 Token ring network controller: IBM 16/4 Token ring UTP/STP controller (rev 66)
00:0c.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]


```


i assume it is BCM4318?

---

### Post by blackzmage on 2009-03-02
which tutorial do i use?

---

### Post by blackzmage on 2009-03-14
-Bump-

i still need help, i have no internet at all, also i updated the specs

---

### Post by thepoplin on 2009-03-17
Same here. I'm in the exact same boat and - yes - I have googled the hell out of the topic. I do not want to ndiswrapper it because I know there is a real solution out there but I am having trouble with it. Apparently some folks had some luck doing it easily in Debian, so why not a Debian based Ubuntu?

---

### Post by ugm6hr on 2009-03-17
You need the b43 driver / firmware.

Unfortunately, installing this without wired ethernet (or some other connection) is not straightforward (i.e. more than just a few clicks), since you have to download all the components of the driver and install manually.

Follow the advice here: [http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)

---

### Post by nukz on 2009-06-30
> **ugm6hr said:**
> You need the b43 driver / firmware.

Unfortunately, installing this without wired ethernet (or some other connection) is not straightforward (i.e. more than just a few clicks), since you have to download all the components of the driver and install manually.

Follow the advice here: [http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)



Have you corrected your problem,  I am also encountering the same problem.

Can you help me with this .

---

