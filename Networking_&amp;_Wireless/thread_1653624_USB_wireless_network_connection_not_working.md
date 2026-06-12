---
title: "USB wireless network connection not working"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by HIRDLS on 2010-12-27
I had a problem connecting to my router/modem using a Netgear (WG111v3) USB wireless adaptor recently. The problem was that the connection would not accept the WPA key. I tried many of the suggestions listed in these fora, but nothing seemed to work. I was running ubuntu 10.04.
 
I had two other computers connected to the same router using the same type of USB adaptor, so was convinced there was nothing wrong with router or the USB adaptor. 
 
In the end I discovered what was causing the problem. The Router Manager software has a setting called Wireless Mode, which can be set to allow the network to operate in g & b mode, g only, b only, etc. I had set this option to "up to 270Mbps" and it was this that was causing the problem - but only with the computer running ubuntu 10.04.  When I set the wireless mode to "up to 130Mbps" it started working again! The router is a Netgear DGN2000.
 
 
The wireless usb driver used was the default rtl8187. I guess there must be something about this driver that doesn't like the higher data rates? Don't know whether this is a bug or just a limitation of the driver, but I hope the above information will be of use to someone.

---

