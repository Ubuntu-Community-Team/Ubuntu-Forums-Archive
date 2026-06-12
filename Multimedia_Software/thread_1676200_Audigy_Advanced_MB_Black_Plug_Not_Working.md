---
title: "Audigy Advanced MB Black Plug Not Working"
date: 2011-01-26
forum: Multimedia Software
---

### Post by MDSBigPaPa on 2011-01-26
Please be patient as I've had Ubuntu 10.04 installed for a week now and I have a steep learning curve ahead of me.

Syetem:
Dell XPS 400 (9150)
nVidia GeForce 6800
4GB memory
Soundblaster Advanced MB Audio
Dell 5650 5.1 Surround sound speaker system with subwoofer
etc,...

Here's a list from lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0c)
05:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem


Herein lies my problem: the black cable output is not working.  I have a 50' extension cable from the black jack to my receiver for my speakers in the living room and also wired to my deck.  The jack works in Windoze but not with Ubuntu.  I'm wondering if it's a configuration issue that escapes me.

Thanks, 
Mark

---

### Post by gordintoronto on 2011-01-26
Run Preferences/Sound, select the Hardware tab, there's a drop-down list with many entries, I think the solution is there somewhere.

---

### Post by MDSBigPaPa on 2011-01-27
Unfortunately, I've already been through all or the possible configurations and have no luck with the black plug yet.

---

### Post by MDSBigPaPa on 2011-01-30
I found a work-around for my problem by using my three-to-one audio pigtail.  It's a pigtail with a green, yellow and black jack that combine into the green plug.  So I can plug into the green jack and get the black audio output to work to my receiver.  However, it's not my preferred solution so any additional feedback on how to get the black lack on the back of my pc working will be helpful.

---

