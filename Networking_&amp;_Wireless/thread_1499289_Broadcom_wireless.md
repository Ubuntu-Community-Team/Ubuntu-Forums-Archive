---
title: "Broadcom wireless"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Shazzam6999 on 2010-06-01
Alright, I've never had any problems connecting to wireless before and I don't seem to be able to find the fix for this.

I'm using a Broadcom Corporation BCM4312 802.11b/g (rev 01) wireless chip in an Acer Aspire 5515. I downloaded the Broadcom STA wireless driver and my computer detects the wireless chip. But thats where the fun ends, I can't see or connect to any other wireless networks. This is the output of iwconfig

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
When I try and scan networks it tells me that the interface does not support scanning. I can even connect to my network if I connect to a hidden network. It assigns me an ip address and everything but I have no connection beyond that.

I really don't know what the problem is, I appreciate any help  :).

---

### Post by pdc on 2010-06-02
try this diagnostic script written by a linux enthusiast in Germany

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English)

it will offer solutions; if they are not enough, please post the data back here

---

