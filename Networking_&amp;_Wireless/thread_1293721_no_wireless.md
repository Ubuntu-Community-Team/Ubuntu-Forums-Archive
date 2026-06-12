---
title: "no wireless"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Kognit on 2009-10-17
Hi

I know that this is quite used topic and have a lot of answers but i just cannot connect to wireless network. I have ubuntu 9.04. Please help?

---

### Post by chili555 on 2009-10-17
Please check here: [http://ubuntuforums.org/showpost.php?p=6183681&postcount=1](http://ubuntuforums.org/showpost.php?p=6183681&postcount=1)

---

### Post by Kognit on 2009-10-18
> **chili555 said:**
> Please check here: [http://ubuntuforums.org/showpost.php?p=6183681&postcount=1](http://ubuntuforums.org/showpost.php?p=6183681&postcount=1)

thx for reply but i still didn't figure it out.

Any other suggestions?

here is my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

### Post by chili555 on 2009-10-18
> 02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)This is your wireless card. A search of this forum suggests that you walk over to an ethernet connection and open a terminal and do:```
sudo apt-get install linux-backports-modules-jaunty
```Restart the computer and your wireless should be working. Please post back if you get stuck.

---

### Post by Kognit on 2009-10-18
> **chili555 said:**
> This is your wireless card. A search of this forum suggests that you walk over to an ethernet connection and open a terminal and do:```
sudo apt-get install linux-backports-modules-jaunty
```Restart the computer and your wireless should be working. Please post back if you get stuck.

You won't believe it. 5 minutes before i looked your post i just did the same - i found it on the net. Thx any way i really appreciate it for your help. 

Kognit

---

