---
title: "Wireless Problems rtl8180"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by yavez on 2009-01-23
Hoping someone can help because I'm going through the ringer on this one.

The default rtl8180 driver for my Realtek 8185 chipset PCI wireless card connects for a few seconds at a very low rate (5 - 8%) then disconnects.  It then goes into a cycle of trying to reconnect without end.  Occasionally it will ask again for the passkey (using 64bit HEX WEP) and then continues the cycle over again.

I decided to go the ndiswrapper route, which works for a while.  75% connection, full speed as tested on speedtest.net, then suddenly it will stop allowing traffic to the internet and across the network, even though I'm still associated and connected to the AP.  To get the internet/networking back I have to either reboot the computer or issue a 

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

and then the connection returns.

So far I have tried several different versions of the Realtek Driver, in case that was the problem, but the same behaviour continues.

What I'd like is to use the native rtl8180 driver if possible, but if not I would love to hear from anyone who has a clue about what's happening with NDISWRAPPER.   

Thanks in advance

---

