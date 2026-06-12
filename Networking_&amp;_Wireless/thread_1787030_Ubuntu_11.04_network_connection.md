---
title: "Ubuntu 11.04 network connection"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by Malificus on 2011-06-20
Hi Guys, 

I have installed 2x Dlink DFE 580TX quad port ethernet cards.

Strange thing is that when I connect  one of the nics, it does not auto detect the connection. I am trying to connect it to a cisco switch. The switch end is live and working but there is nothing connected within the Ubuntu OS.

I have also tried to connect one of the nics to my broadband router and that does not work either, if i run a lspci from terminal is shows the following, 

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 PCI bridge: Intel Corporation 21152 PCI-to-PCI Bridge
05:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
06:04.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 14)
06:05.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 14)
06:06.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 14)
06:07.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 14)
07:04.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)
07:05.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)
07:06.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)
07:07.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)


What is really interesting is that if i connect my broadband router to my on board nic card, it works fine. These cards use to work on Ubuntu 10 but i am having trouble in 11.04, any ideas? 

I have also not installed any software with regards to these NIC cards, ubuntu already detected them.

any help would be great.

---

### Post by Malificus on 2011-06-21
anyone got any ideas?

---

