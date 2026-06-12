---
title: "Lost internet (maybe hardware problem?)"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by tunin on 2009-06-28
First of all, I have a dual boot system.  I have 2 separate drives having ubuntu 7.10 on one, and 9.04 on the other.  I have an A7V8X-X motherboard with onboard lan.  Suddenly I have no internet from either os.  I suspected the isp, but since I live above where I work and work has the same isp (different account), I rerouted wires to try both connections on both computers.  Both work fine on the work comp, but nothing on mine.

I decided to try sticking in a pci network card, but it isn't being recognized as far as I can tell.  The following info is from the 9.04 install.

> lorin@tunin-toy:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0b.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

networking is showing it as (pan0)

Bye the way, I have disabled the onboard lan in bios. When enabled, it shows in this list, but doesn't do anything.

Since I am having to save and transfer things on a thumb drive, I may not be real fast getting back, but I would appreciate where to go, or what to check from here.  I am assuming that something has happened to the onboard lan part of the MB, but I'm not sure if that would interfere with an added on pci lan?  I am way out of my depth, so any suggestions would be welcome.

---

### Post by jhannah on 2009-06-28
The pan0 interface is actually a virtual bridge that is used with Bluetooth PANs. If you have Bluetooth support (and even don't have any Bluetooth hardware) the device will show up but it can safely be ignored.

It sounds like your machine isn't recognizing the NIC at all. What type of PCI NIC is it that you are installing and what type of NIC do you have built in? It sounds like the NIC might not be working correctly or is not supported although I doubt that is the case.

Does either NIC show up in the output of 'lspci' or 'ifconfig -a' in either installation of Ubuntu?

---

### Post by tunin on 2009-06-30
Ok, I enabled the onboard lan in bios, and now lspci shows the onboard:

> lorin@tunin-toy:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
00:0b.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)


With the hardware manager of 7.10, it shows it as a VT6102 (Rhine-II) Networking interface.  I don't see a place to get a hardware list on 9.04 to see if it is shown there.  the 7.10 lspci outputis identical to what is shown above from 9.04.  

The add on that so far is unrecognized is:
Edimax IEEE-802.3 10/100Base-TX 
Fast Ethernet PCI Adapter

Any idea why that shows as a bluetooth component?  I have some screenshots of network manager and settings pages, but I need to get them hosted and post a link.  I'll do that as soon as I have a chance.

---

### Post by tunin on 2009-06-30
In case they give any needed info, the screenshots are at:
[http://cid-b6c02304ea92926c.skydrive.live.com/browse.aspx/Network%20issue](http://cid-b6c02304ea92926c.skydrive.live.com/browse.aspx/Network%20issue)

---

