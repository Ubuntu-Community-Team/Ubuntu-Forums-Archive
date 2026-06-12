---
title: "Erratic Internet Speeds :("
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by crucialhoax on 2009-11-06
Hello all.

I'm very new to ubuntu and I'm using an HP dv4 laptop running 9.10 Karmic Koala x_64. I've at least traced down my issue, its not a DNS issue, yet its a connection speed that won't hold. I didn't have this issue what so ever in Vista but thats a whole different environment.

Pretty much what I do know is that I can't keep a fast connection. It goes from 2mb/s to 53mb/s then back so on and so forth. Very annoying.

lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: **Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

bold is my current wireless connection.

Any help is greatly appreciated. I have also taken screenshots of this mess lol.

---

### Post by papangul on 2009-11-06
You could try this solution:
[http://ubuntuforums.org/showthread.php?t=1316012](http://ubuntuforums.org/showthread.php?t=1316012)

---

### Post by crucialhoax on 2009-11-06
Perfect I'll give it a try. Its not a driver issue?

---

### Post by crucialhoax on 2009-11-07
Looks like that fixed it. Thank you so much :)

---

### Post by papangul on 2009-11-07
Please consider marking the thread as 'Solved'

---

### Post by crucialhoax on 2009-11-07
Just did it. Again thanks so much. I actually like Wicd better. Easier to use and has more features :)

---

