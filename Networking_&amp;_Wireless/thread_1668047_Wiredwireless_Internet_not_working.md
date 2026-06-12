---
title: "Wired/wireless Internet not working"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by ScarfofSexualPreferance on 2011-01-15
I'm running Windows 7 and Xubuntu 10.10 on a dell pc.
 
My wireless works fine when I run windows 7, but on Xubuntu, the wireless doesn't even come as an option. When I try to plug in the wired connection, it loads for about a minute then tells me I'm disconnect. The option for the wired connection is there, but when I try to click it, the same thing happens. What do I do?

---

### Post by gordintoronto on 2011-01-15
Open Accessories/Terminal and run this command:
lspci

Then copy/paste the output here. There are about a million configurations of Dell PCs, and this will display what actual devices you have.

By the way, a machine that runs Windows 7 can run a better version of Ubuntu than Xubuntu.

---

### Post by ScarfofSexualPreferance on 2011-01-16
[SIZE=3][FONT=Times New Roman]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
 
 
 
And what do you think's better than xubuntu?

---

### Post by gordintoronto on 2011-01-16
The Marvell is your wired Ethernet controller. To investigate why it doesn't work, I would Google 88e8040 linux

I'm pretty sure a driver for the Broadcom wireless could be installed in about four mouse clicks, if you could get a wired connection.

If your Dell is a netbook, I would use the netbook edition of Ubuntu. If it's a regular laptop, I would use regular Ubuntu. Or even Linux Mint, which is derived from Ubuntu, and gets you up and running a wee bit faster. Mint might even have the wireless driver included in the CD image.

---

### Post by mathia on 2011-01-17
Which kernel is in use?
$ sudo uname -a

---

### Post by mathia on 2011-01-17
Which drivers are in use?
$ sudo lsmod

---

### Post by ScarfofSexualPreferance on 2011-01-22
I tried installing linux mint, but I need internet for the drivers too. Is there anyway that I could install them from a flash drive?

---

### Post by mathia on 2011-01-24
Hi,
for your wired LOM on ubuntu ( you can download it with win 7), please install the following ethernet driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

P.S.: This driver works for linux kernel versions < 2.6.35!
There is also a workaround for kernel version > 2.6.35.

---

