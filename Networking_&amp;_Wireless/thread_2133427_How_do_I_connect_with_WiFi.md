---
title: "How do I connect with WiFi?"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by gga96 on 2013-04-08
Hi All.

I now have MythBuntu installed and a remode frontend working on a wired Ethernet, all working well. 
The frontend is a Asrock ion 3D 152d and I would like to establish a WiFi connection to the Netgear N150 Router.
I have removed the the cable from both frontend and router, rebooted, but no wifi connection.
I am currently back to wired to write this post.

The following may help:
> 
glen@Frontemd-L:~$ uname -a
Linux Frontemd-L 3.2.0-39-generic-pae #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 i686 i686 i386 GNU/Linux
glen@Frontemd-L:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)


The wired connection and remote worked well out of the AsRock box. Not so with the wireless connection.

I have little knowledge of ubuntu and will be very greatfull for a detailed procedural solution or a little black magic.

Thank you
Glen

---

### Post by gga96 on 2013-04-08
After 2 days googling I have just found Network Manager.

Great! But I dont kmow the answer to BSSID.

How do I get the nn:nn:nn:nn:nn:nn number?
Am I IPv4 or IPv6?

---

### Post by Laiquendi on 2013-04-08
Your question is confusing me...
The easiest way is to connect by clicking on the name of the Wi-Fi network you want to join. if you do not see the network name then it is hidden or you have some configuration problem.
If it is hidden, you simply go into "Wireless" tab in the Network Manager, click "Add" and put in the SSID the hidden network name (like for example MyHomeNetwork) and the password in "Wireless security" tab. You do not need to fill the rest of the fields.

---

### Post by gga96 on 2013-04-08
Good morning Laiquendi.

Thank you for your help.

I deleted my last attempt and started again with "Add".  Followed your instructions and the connection was made.

Simple when you know how.

Thanks again.
Glen

---

### Post by Laiquendi on 2013-04-09
Happy to help :)
Now you should change the topic into "Solved".
> To mark your thread solved, go to _[COLOR=Red]Thead Tools[/COLOR]_ and select "Mark this thread as solved"

---

### Post by gga96 on 2013-04-09
Hi,
Are you refering to Thead Tools at the top right of this page, if so it does not have a "Mark this thread as solved", but I have heard that this functionallity is on its way.

---

