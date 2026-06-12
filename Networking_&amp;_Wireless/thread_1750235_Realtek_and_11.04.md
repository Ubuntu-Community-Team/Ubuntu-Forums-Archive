---
title: "Realtek and 11.04"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Grisk13 on 2011-05-05
Hello, all!  First time poster!

The problem:

I recently upgraded to 11.04 and I am pleased, overall, with the move.  That said I am having some trouble with my wireless card.  When I first installed Natty, I had WiFi no problem, but after one reboot, I am unable to connect to my local WiFi network!  I can still see all available networks, so I think the card is posting properly, but when I try to connect to my home network, I am asked repeatedly for my WEP key.  The computer will ask for the key, attempt to connect for around 5 minutes, then ask for it again.  

Before anyone asks, yes, I made sure the WEP key was correct, it actually worked before in Ubuntu and it works currently on a laptop (Alienware M15x) and a desktop (the one in question) in Window$.

My hardware:

I did some digging, here is the hardware in question (I think).  

lspci:
[FONT=Times New Roman][SIZE=2]0c:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)[/SIZE][/FONT]

lshw -C network
[FONT=Times New Roman][SIZE=2]
description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: bc:ae:c5:23:ae:ed
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:f7bf0000-f7bfffff[/SIZE][/FONT]

[FONT=Verdana]What I've tried:

My research shows that the drivers for this card exist in Ubuntu, but, for some reason, the OS is using the incorrect driver.  This should be as simple as compiling the correct driver and installing it, but I tried to install: r8168-8.023.00, which I have read should be compatible, from realtek's site and that has yet to fix the problem (I actually don't notice that driver appearing anywhere in the lswh command, does that mean it didn't install at all?)

Conclusion:

Thanks for reading, I hope someone can help me sort this issue out.  I am a student (Math/CS) and I have been hoping to finally make the full switch to Linux over the summer, as  I have been fooling around with Ubuntu for about a year now.
[/FONT]

---

### Post by chili555 on 2011-05-05
> description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth0
version: 03
serial: bc:ae:c5:23:ae:ed
size: 10Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
resources: irq:50 ioport:c800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:f7bf0000-f7bfffff
This is ethernet, not wireless.> lspci:
0c:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
Can you please post:```
lspci [COLOR="Red"]-nn[/COLOR]
```Thanks.

---

### Post by Grisk13 on 2011-05-05
All I can say is whoops!  

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1c.6 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 [8086:3b4e] (rev 06)
00:1c.7 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 [8086:3b50] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b02] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Barts XT [ATI Radeon HD 6800 Series] [1002:6738]
01:00.1 Audio device [0403]: ATI Technologies Inc Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]
03:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
06:00.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:01.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:05.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:07.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
07:09.0 PCI bridge [0604]: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch [10b5:8608] (rev ba)
08:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
09:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Device [1b4b:91a0] (rev 12)
0c:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
0c:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
is the command you asked for and 


1a/b/g Wireless LAN Controller (rev 20)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

is what I meant to post.  It doesn't even show Realtek, even though the card is, which makes me think that the card is not being recognized at all.  How can that be, though, if I can view wireless networks (just not connect)

Thanks for the help!

---

### Post by deuz on 2011-05-05
You can try this [http://ubuntuforums.org/showpost.php?p=10773821&postcount=9](http://ubuntuforums.org/showpost.php?p=10773821&postcount=9)

(ofcourse replace wlan0 etc. if they are different)

---

### Post by Grisk13 on 2011-05-05
When I run the scan, it actually displays the correct SSID, but doesn't connect to it (by that step, I should be connected, right?)

The connection is reading unblocked (either "soft" or "hard"), so I really have no idea what is going on :(

---

### Post by william.smith3 on 2011-05-05
Try using the wireless utility in the panel, do you see your network there?

---

### Post by Grisk13 on 2011-05-05
I can, indeed, "see" the network, bu I am unable to connect to it.

Update:  I've been doing more digging and I found this:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

This is a link to what I *think* is the correct driver, but it is out of date (it mentions Ubuntu 6 in the documentation.)  I gave it a go anyway, and I was able to make and make install it.  It is also reporting that it is working (when I tried to insert a "r81585.ko" file they told me to, I got a "file exists" error, and the documentation says that means it installed properly.  The problem is that it still doesn't work.  

Anyone have anything else to add?  I'm extremely confused, but I'm still new to this, so the documentation I am working on is a bit hard for me to read.  Only one way to learn, though ;)

UPDATE:

I figured it out!  or... kinda did.  There appears to be a problem with the version of a script that the make-install has from the driver I linked earlier.  The driver actually works, but you have to run wlan0down and wlan0up after using makeinstall (in that order) to get a fresh script.  I've been able to reboot and actually have wireless working, so I am pleased :D  Posting from the desktop in question right now!

---

