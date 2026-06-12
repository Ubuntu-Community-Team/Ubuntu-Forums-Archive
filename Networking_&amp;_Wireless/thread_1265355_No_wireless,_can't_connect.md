---
title: "No wireless, can't connect"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by g-raf on 2009-09-13
I just reinstalled Ubuntu Studio 9.04 on my toshiba satellite a300 laptop. Everything works great and the reinstall solved problems for me. However, I now have no internet connection. I usually use wireless, but now i'm hooked up to a cable for the time being. I'm guessing that i might need to install drivers or something for the wifi chip. The network manager says under both wired and wireless networks, "device not managed." 

I checked my wifi chips in the terminal and this is what i got:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1bcf:0007 Sunplus Innovation Technology Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I'm trying to hook this up quick. Please help. Thanks.

---

### Post by Bucky Ball on 2009-09-13
In terminal:

lspci

Post back

---

### Post by g-raf on 2009-09-13
This is what i got:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
04:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
04:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
04:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by g-raf on 2009-09-13
I've read somewhere that the Intel Wifi Link 5100 has problems on Jaunty. Any idea of how i can get it going?

---

### Post by Bucky Ball on 2009-09-13
Realtek RTL8101E/RTL8102E is what you should be looking for.

---

### Post by g-raf on 2009-09-13
Ok i finally got that Realtek driver started up and working. I read manuleka's advice on this link: [http://ubuntuforums.org/archive/index.php/t-1054480.html](http://ubuntuforums.org/archive/index.php/t-1054480.html)

They said:

"unpack your download... 

in terminal go to the unpacked folder then run these commands

[NOTE: i'm using RTL8101E and Ubuntu 8.10]


sudo -E make clean modules  
sudo make install  
sudo depmod -a
blacklist r8169
sudo update-initramfs -u"

I hope running these commands will help others who are trying to get their wifi hooked up as well. Case closed!

---

### Post by Bucky Ball on 2009-09-13
Excellent work. I do believe the 'Solved' function is once again available under 'Thread Tools'.

---

