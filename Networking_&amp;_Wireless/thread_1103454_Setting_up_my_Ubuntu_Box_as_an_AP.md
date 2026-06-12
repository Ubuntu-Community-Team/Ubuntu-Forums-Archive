---
title: "Setting up my Ubuntu Box as an AP"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by utumno4 on 2009-03-22
So, as the title says, I'm trying to set up my ubuntu box as an ap. 

I'm getting snagged trying to get ap (master) mode enabled on my card(s). 

I have two candidate cards, but so far the research I've done seems to indicate that I should have the best luck with my Belkin F5D7000. I also have a Linksys WMP54G card at my disposal.

The Belkin uses the  Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) chipset.

I've been messing around with the documentation on [http://www.linuxwireless.org](http://www.linuxwireless.org) to no avail. Any help/pointers would be greatly appreciated.

---

### Post by Iowan on 2009-03-23
I found [this]("www.experts-exchange.com/OS/Linux/Q_24148784.html") link (which wouldn't open for me), but it also contained [this]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint") link.

---

### Post by utumno4 on 2009-03-24
So, after doing some more digging, I downloaded the hostapd package from linuxwireless.org which had nl80211 support. I also downloaded the newest compat-wireless drivers from there. I followed some tutuorials, messed around, and finally got my linxsys wireless card to do master mode.

But now my system freezes. Randomly. I say 'randomly,' but in reality it used to be random, it could've happened right after login, or in hours. Now the system freezes as soon as it can, basically. Either on the login screen or immediately post log-in.

---

