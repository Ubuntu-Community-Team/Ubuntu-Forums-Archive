---
title: "Please help!  PCI or USB, your choice!"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by ZeroRider13 on 2011-01-14
Hey guys, I have the dreaded WG111T USB Dongle, and the not so infamous Linksys WMP11 PCI Card.  I have tried for three and a half hours now for connectivity on either one with nothing to show for it.  I really need your help, I don't care which one it's for, but I need your help!  Thank you sooo much.

Edit:
I will be adding more info such as lspci and more, anything you need ask for it please, as of now, I am currently installing a fresh 10.10 so nothing has been changed, it is a desktop, and it is a Dimension E520...I know =[

---

### Post by ZeroRider13 on 2011-01-14
Please help guys, I'm really trying to get this to work out, I have a fresh install, I just need to know what to do from their =]

---

### Post by gordintoronto on 2011-01-14
Providing output from lspci and lsusb would make it easier for people to help you.

If you can possibly get a hard-wired connection for a few minutes, you could run Administration/Additional Drivers to see if you could install a relevant driver.

---

### Post by gordintoronto on 2011-01-14
Also: if you can possibly get a hard-wired connection for a few minutes, you could run Administration/Additional Drivers to see if you could install a relevant driver.

---

### Post by gordintoronto on 2011-01-14
Also: if you can possibly get a hard-wired connection for a few minutes, you could run Administration/Additional Drivers to see if you could install a relevant driver.

---

### Post by ZeroRider13 on 2011-01-14
Okay, finally able to get it.  By the way, blind luck, I had a fresh install of 10.10 so I transferred the .inf files and got ndiswrapper common, utils, and ndisgtk, loaded it up, and I was able to see wireless networks.  THis only happened once before, and then when I restarted it, it was gone, and wouldn't work again.  THe only problem is, I know I can connect to these networks because I have in the past, but it just continues to animate the signal, and eventually tell me that it couldn't connect.  Especially with my home WEP key which it keeps asking me for, but I know is correct.  Well here are the outputs:


family@FamilyRoom:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
family@FamilyRoom:~$ 
family@FamilyRoom:~$ lsusb
Bus 007 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 1385:4250 Netgear, Inc WG111T
Bus 002 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 002 Device 003: ID 03f0:3307 Hewlett-Packard 
Bus 002 Device 002: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
family@FamilyRoom:~$

---

### Post by SeePU on 2011-01-14
> **ZeroRider13 said:**
> Hey guys, I have the dreaded WG111T USB Dongle, and the not so infamous Linksys WMP11 PCI Card.  I have tried for three and a half hours now for connectivity on either one with nothing to show for it.  I really need your help, I don't care which one it's for, but I need your help!  Thank you sooo much.

Edit:
I will be adding more info such as lspci and more, anything you need ask for it please, as of now, I am currently installing a fresh 10.10 so nothing has been changed, it is a desktop, and it is a Dimension E520...I know =[I was looking at buying a Netgear WG111T USB dongle because  I was told it's an out of the box configuration.  You can't get it to work?!?  What version is it?  I read that version 2 has the Atheros chipset and version 1 has a Marvell chipset which isn't supported at all in Linux.

You check this site for the versions of the Linksys and the corresponding chipset but you have to figure out the version / chipset to know what to do.

[http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)

Read this and see if the tips therein help:
[http://www.aircrack-ng.org/doku.php?id=compatible_cards#determine_the_chipset](http://www.aircrack-ng.org/doku.php?id=compatible_cards#determine_the_chipset)

Sorry for the edits.

---

### Post by SeePU on 2011-01-14
I'm thinking of the WN111!  Ooops.  Your WG111T still has an Atheros chip, though.

Edit:  A google search seems to indicate it's an Atheros Atheros 5523 chipset.  No wonder you're having trouble.  It's the old Madwifi project or something that used to contain the support but I am not sure what you'd do now.  Do a search for your Netgear adapter in the forums and the Atheros 5523 chipset.

---

### Post by ZeroRider13 on 2011-01-14
Yeah, do a quick lookup on WG111T ubuntu problems...unfortunately it is THE dongle not to get.  It is also very cheap, and I'm on a budget so I thought one way or another I could get it to work.

Ehh, I'm sorry but could you be a little more specific?  I think you're helping me with the pci card, right?  I'm sorry, I'm not very good with pci cards so I'm totally lost.

---

### Post by SeePU on 2011-01-14
> **ZeroRider13 said:**
> Yeah, do a quick lookup on WG111T ubuntu problems...unfortunately it is THE dongle not to get.  It is also very cheap, and I'm on a budget so I thought one way or another I could get it to work.

Ehh, I'm sorry but could you be a little more specific?  I think you're helping me with the pci card, right?  I'm sorry, I'm not very good with pci cards so I'm totally lost.In post #7, I'm helping with your pci card.  Can you click that link and read the info?  Where it states to run lsusb (which you did) but if you don't get the chipset info, it states to run hwinfo and dmesg.

I would run dmesg command and see what it displays for your pci info - is your network card installed?  If your pci wifi network card is installed, the linksys one, see if dmesg gives more info i.e. on the chipset.

It should give more info on the usb wifi dongle, too.  Reboot and run dmesg after, if necessary.

---

