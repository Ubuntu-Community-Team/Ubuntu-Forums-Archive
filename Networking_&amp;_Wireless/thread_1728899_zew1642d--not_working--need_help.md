---
title: "zew1642d--not working--need help"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by ktjrk on 2011-04-14
If I Could have assistance plz

---

### Post by chili555 on 2011-04-14
Please post:```
lspci -nn
```What have you tried so far?

---

### Post by ktjrk on 2011-04-14
keith@keith-System-Product-Name:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3300 Graphics [1002:9614]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
04:06.0 Network controller [0280]: RaLink Device [1814:3062]
keith@keith-System-Product-Name:~$ 





ive tried sum of the basic blacklisting that i saw in other post but nothing worked

---

### Post by chili555 on 2011-04-14
Here is what you need to do. Post back if you get stuck.

[http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/)

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Be sure to get the latest version, 2.4.1.1. RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)

---

### Post by ktjrk on 2011-04-14
im stuck where it says build it by typing make in the main archive.......where would i type it?

---

### Post by chili555 on 2011-04-14
Open a terminal and navigate to the location where you downloaded the file, for example:```
cd Desktop/RT3562whatever
sudo su
make
make install
modprobe rt3562sta
exit
```

---

