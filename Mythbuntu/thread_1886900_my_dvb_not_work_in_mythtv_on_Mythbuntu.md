---
title: "my dvb not work in mythtv on Mythbuntu"
date: 2011-11-25
forum: Mythbuntu
---

### Post by khlead on 2011-11-25
hey 

i have dvb (Azurewave AD-SP 410)

dont work 


dmesg | grep -i dvb

not work

gg@gg:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
[COLOR="Red"]03:06.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)[/COLOR]

i need help for Driver Card

---

### Post by joshoekstra on 2011-11-25
It seems you have a card that isn´t supported yet if I look at this page:
[linuxtv.org]("http://www.linuxtv.org/wiki/index.php/DVB-S2_PCIe_Cards")
It also tells you how to get it supported, if you can i'd replace it with a supported card.

---

### Post by khlead on 2011-11-25
me card DVB-S not DVB-S2

---

### Post by klc5555 on 2011-11-25
Twinhan cards historically are badly supported on Linux. According to linuxtv.org ( [http://www.linuxtv.org/wiki/index.php/TwinHan](http://www.linuxtv.org/wiki/index.php/TwinHan) ), Twinhan does not provide source for their drivers, and provided binary support for only some of their cards with some kernels in Linux in 2007. It's not clear whether these closed-source binary drivers are still available, or whether they were ever available for the AD-SP 410, or, if available whether they work on contemporary systems.

In short, I suspect that the AD-SP 410 is currently unsupported on Linux, with no clear indication of whether it will ever be supported.

However, some drivers have been written for the Mantis family of DVB-S cards, including the AD-SP300. Found here: [http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards)  I suppose it's marginally possible one of these may work on the 410 as well.

Otherwise, you may need a better-supported card.

---

