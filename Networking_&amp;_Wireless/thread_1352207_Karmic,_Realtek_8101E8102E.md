---
title: "Karmic, Realtek 8101E/8102E"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by hermpes on 2009-12-11
Hey there, just installed 9.1 and am having trouble with the wireless from this Realtek 8101E/8102E card. 

I can connect to my network fine, but after downloading a few mb of an update the internet bottoms out.
Wired mode works perfectly, just the wireless is screwy. I have been attempting to use ndiswrapper but I cannot find a driver that will work with it. I have tried every single driver from the realtek website, but i only get missing symbol errors from 
dmesg | grep -e ndis -e wlan 
does anybody know of a working driver for this particular piece of hardware?
> Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136]

---

### Post by hermpes on 2009-12-11
bump. please!

---

### Post by chili555 on 2009-12-11
> trouble with the wireless from this Realtek 8101E/8102EI believe this is an ethernet card, not a wireless card. How about letting us see the entire *lspci*.

---

### Post by hermpes on 2009-12-11
took a step back and did lsusb and found my wireless card. tried windows drivers in ndiswrapper still didnt work

> Bus 001 Device 001: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

UPDATE: solved by blacklisting competing driver. thanks for your help!

---

### Post by tnadawg89 on 2010-02-07
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
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
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

---

### Post by chili555 on 2010-02-07
> Device 8172 (rev 10)Please see: [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

---

