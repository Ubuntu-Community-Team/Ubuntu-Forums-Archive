---
title: "NetGear WNA1000M Not Working."
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by CGUI on 2011-09-18
I have a HP DV6000 with Natty. I picked this for next to nothing and the HDD was wiped so I decided I wanted to mess around with Ubuntu a little bit. I have everything working on this machine except the wireless. It has an onboard Broadcom, but after hours beyond hours of trying to get that configured, I still had no luck. I think the wireless card port on the mobo itself maybe dead. However, I just bought a WNA1000M just to get it on wireless again, but I can't seem to get this working either. I doesn't show any networks to connect to. When I run a lsusb in terminal it shows:

Bus 001 Device 004: ID 0846:9041 NetGear, Inc.

---

### Post by think13 on 2011-09-18
This forum post seems to solve the same problem you are having. 
[http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M](http://ubuntuforums.org/showthread.php?t=1806839&highlight=WNA1000M)
Please go there and let us know if you have any trouble.

---

### Post by CGUI on 2011-09-18
The link to the tarball file seems to be dead. I found a bunch of the compat-wireless .tar on Linuxwireless.org. Can you proivde a link to the correct one what version number I should download?

---

### Post by CGUI on 2011-09-18
Anyone have another link to download the file that chili is talking about in the 6th post?

---

### Post by think13 on 2011-09-18
Looks like kernel.org is down for maintenance. You can try this link:
[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2)

---

### Post by CableCat on 2012-02-28
Mini USB wifi adaptor that work in Ubuntu:
* Buffalo AirStation N-Technology 150Mbps USB 2.0 Client [WLI-UC-GNM-EU]

Mini USB wifi adaptors that do not work in Ubuntu:
* NETGEAR G54/N150 Wireless USB Micro Adapter WNA1000M [WNA1000M-100PES]
* TRENDnet TEW 648UBM [TEW-648UBM]
* D-Link Wireless N 150 Micro USB Adapter DWA-121 [DWA-121]
* Belkin N150 Micro Wireless USB Adapter [F7D1102AZ]

Tested at 2012-02-28 in Ubuntu 11.10 and Daily Live.
Connecting to WPA2 enterprise network fails most times.

[IMG]http://kom.aau.dk/~pmr/www/mini_USB_WIFI/Mini_USB_WIFI_in_Ubuntu_550px.png[/IMG]

---

### Post by bleers on 2012-11-15
About: Buffalo AirStation WLI-UC-GNM-EU

Can anybody confirm this USB wifi-adapter really works under Ubuntu 12.xx ?
Are there any connection drops or speed issues?

---

