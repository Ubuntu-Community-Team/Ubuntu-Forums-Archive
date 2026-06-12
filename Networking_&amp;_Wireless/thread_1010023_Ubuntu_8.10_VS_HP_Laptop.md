---
title: "Ubuntu 8.10 VS HP Laptop"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by anti-l33t on 2008-12-13
I just setup Ubuntu 8.10 on my laptop and I can't seem to get the wireless networking to work.  The laptop is an HP G50-111NR.  I'm running 8.04 on my desktop and have no issue, but the networking apps seem to be a little different in 8.10 and I'm not very smart.  Can anyone help me out?

---

### Post by Ayuthia on 2008-12-13
> **anti-l33t said:**
> I just setup Ubuntu 8.10 on my laptop and I can't seem to get the wireless networking to work.  The laptop is an HP G50-111NR.  I'm running 8.04 on my desktop and have no issue, but the networking apps seem to be a little different in 8.10 and I'm not very smart.  Can anyone help me out?

Can you go into the Terminal and post the results of lspci -nn?  We need some help in identifying your wireless card.

---

### Post by anti-l33t on 2008-12-13
michael@michael-laptop:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03) 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) 
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01) 

I've also noticed that the wireless button turns red (red is off, blue is on) when Vista shuts down and stays red the entire time I'm in Ubuntu.  It seems like Ubuntu just doesn't know how to turn it on.

---

### Post by falcon61102 on 2008-12-13
Does your system require the use of restricted drivers?  You can check by going to System>Administration>Hardware Drivers.  Check to see if your card is listed and attempt to enable it if it is.

---

### Post by anti-l33t on 2008-12-13
> **falcon61102 said:**
> Does your system require the use of restricted drivers?  You can check by going to System>Administration>Hardware Drivers.  Check to see if your card is listed and attempt to enable it if it is.

My card is listed, but it's already enabled.

---

### Post by falcon61102 on 2008-12-13
I've been looking into problems that users with your card have reported.  There seem to be a couple solutions.  You can install drivers via ndiswrapper and that seems to work well or use madwifi and backports to get it running.  Here are a couple links that should help you.  I've got more experience with ndiswrapper and can help you with that one if you choice to use that and run into problems.

ndiswrapper solution:
[http://ubuntuforums.org/archive/index.php/t-766169.html](http://ubuntuforums.org/archive/index.php/t-766169.html)

madwifi and backports (very long):
[http://ubuntuforums.org/showthread.php?t=894852](http://ubuntuforums.org/showthread.php?t=894852)

---

