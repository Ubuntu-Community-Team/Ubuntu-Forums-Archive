---
title: "reinstalling and video driver problem"
date: 2011-03-27
forum: Multimedia Software
---

### Post by Bobrm2 on 2011-03-27
Have had to reinstall Ubuntu 10.04, destroyed partitions: however my video seems to corrupt when moving the mouse. Control-R will return it to a readable state. Mouse is wireless Logic-tech, if that makes a difference.

   Have tried system/administration/Hwdware drivers, no third party drivers installed, or can't locate it.

   Currently, trying to learn which terminal command will help, has anyone else that this problem. Thanks.

Bob

---

### Post by gordintoronto on 2011-03-27
If you run:
lspci

and look at the line which contains "VGA," it will tell you what video adapter you have. Could you also describe your computer: CPU, memory, BIOS, anything unusual?

---

### Post by Bobrm2 on 2011-03-27
I reinstalled 10.10, and don't seen to have the video problems now. Have lost the min/max/close buttons etc. will address that in another post. Thank you for your response.
 Video Screen is an HPv?2207. 
Bob

bob@Ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:01.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bob@Ubuntu:~$

---

### Post by Yellow Pasque on 2011-03-28
I'd suggest trying updated video drivers to see if the issue has been fixed: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

