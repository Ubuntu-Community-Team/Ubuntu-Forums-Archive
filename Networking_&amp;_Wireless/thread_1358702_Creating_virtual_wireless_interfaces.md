---
title: "Creating virtual wireless interfaces"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2009-12-18
Using the airmon-ng script from the aircrack suite, I can have multiple wireless interfaces based on a single physical wireless card.  In other words, I can have wlan0 working in managed mode and connected to a router, while mon0 is in monitor mode, but both wlan0 and mon0 are based off of the same physical device.

airmon-ng only allows the creation of additional virtual interfaces in monitor mode, but I'm thinking there must also be a way to create additional interfaces in managed mode so that I could have wlan0, wlan1, wlan2, etc. all connected to different routers, but based off of the same wireless card.

I'm having trouble figuring out how to configure this.  If anyone could point me in the right direction, I'd be grateful.  There are several wireless networks in range of my house and I'd like to connect to them all, then use bonding to increase network bandwidth and reliability.

My wireless driver is ath5.

---

### Post by pytheas22 on 2009-12-18
Nevermind, answered my own question.  You can do this using iw (may need to be installed first) with a command like:
```

iw dev wlan0 interface add wlan1 type station
```

This will create an interface named wlan1_rename (I don't know where the "rename" bit comes from; probably something udev is doing).  Unfortunately NetworkManager doesn't seem to be detecting the interface, but it does exist and can scan using "iwlist scan".

---

### Post by sushovan on 2011-05-02
Hi,
After giving the iw command ubuntu gives the following error:
[FONT=Arial Black]nl80211 not found.

[FONT=Verdana]What should I do?[/FONT]
[/FONT]

---

### Post by pytheas22 on 2011-05-02
> Hi,
After giving the iw command ubuntu gives the following error:
nl80211 not found.

What should I do?

Judging from clues in this [bug report]("https://bugs.launchpad.net/ubuntu/+source/iw/+bug/370046"), it seems like that error message means either that your hardware or driver doesn't support AP mode.  Which driver are you trying to use?  Maybe there's an alternative driver that would work better for you.

---

