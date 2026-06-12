---
title: "Dell 1721 / Broadcom 4311 chipset - Trying to change drivers"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by Tempest20 on 2010-07-04
Hi All, I'm new to linux/ubuntu, only had it for a month, and also new  to the forum. I was wondering if anyone could give me some help with  changing some drivers on my system. Hopefully I'm posting in the right  section.

I have a Dell Inspiron 1721 with a Dell 1390 wireless  card in it. It has the **Broadcom 4311 (rev 01)** chipset in it. I'm  also using [B]ubuntu 10.04 (lucid) - kernel 2.6.32-21.

[/B]I'm  trying to activate monitor mode on my wireless card, which I've read  works, but only with the b43 drivers, not the STA drivers.

When I  first installed ubuntu, I activated the Broadcom STA wireless driver,  but have recently found out that it won't get me anywhere when trying to  activate monitor mode, since it's been disabled in this driver (thanks  Broadcom). 

I've installed b43fwcutter, and believe that I have  the b43 drivers in, but am not sure how to get rid of the STA driver and  activate the b43 drivers.

Also, when I scan my system, I don't  recognize a distinction between my wired and wireless card, but is that  simply because I'm not wired in right now, and just using a wireless  connection? This is what I get when I run **iwconfig**
[INDENT]$  iwconfig
lo        no wireless extensions.

eth1      IEEE  802.11  Access Point: Not-Associated   
          Link Quality:5   Signal level:212  Noise level:199
          Rx invalid nwid:0   invalid crypt:29  invalid misc:0

pan0      no wireless  extensions.
[/INDENT]All the tutorials I've read suggested to  edit wlan0, which of course wouldn't work for me, and I couldn't figure  out how to make them work for me.

These are my results when I run  lspci (I've only taken the results pertinent to networking)
[INDENT]03:00.0  Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev  02)
0b:00.0 Network controller: Broadcom Corporation BCM4311  802.11b/g WLAN (rev 01)
[/INDENT]Do I need to post any further  information? Thanks in advance for your help.

---

### Post by Tempest20 on 2010-07-05
I now realize this was a silly question...I figured out how to remove the STA drivers through the package manager, and have the b43 in use instead now.

---

