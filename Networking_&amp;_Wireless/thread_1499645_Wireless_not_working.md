---
title: "Wireless not working"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by PRPR on 2010-06-02
Hi,
I've just installed Ubuntu 10.04 for the first time on my Acer travelmate 2700. Before I was using Windows XP and it used to be quite easy to connect to the internet. When I start XP a light turns on automatically indicating the wireless card is working but this doesn't happen with Ubuntu. When I start Ubuntu I have to turn it on manually but it can't detect any wireless networks. I guess I don't have the Linux driver for my wireless card (IPN 2220 ) but I don't know where to get it nor how to install it if eventually I find it somewhere.
 
Any help would be very much appreciated.
Thanks,
PR

---

### Post by pdc on 2010-06-02
go to Systems (top line at left): accessories; terminal

in that, type

lspci

look for the line says network: use the find function in your browser

it may say

> Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

.. or it may not .. if it does ..

here is a guide to installing broadcom drivers

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

post #9 talks about the 4318, if that is what yours is

if not, post back what you get for network

---

