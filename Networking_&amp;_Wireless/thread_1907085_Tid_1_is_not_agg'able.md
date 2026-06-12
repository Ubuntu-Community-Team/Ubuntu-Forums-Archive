---
title: "Tid 1 is not agg'able"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by Aqlor on 2012-01-10
Hello, 

I've been using my xubuntu distro for some time now with very little problems, however, in the past few days my wireless connection has been failing me. I don't know what is causing this. 

I can connect to wireless networks and go online normally for a while, but after that, I continue connected to the network but I can't establish any connection.

Doing a dmesg gives me a LOT of these in return:

```
ieee80211 phy0: START: tid 1 is not agg'able
```

Any idea on what is causing it and how can I solve it ? (I am guessing it was one of the recent updates that caused this as I had no wireless problems before)

additional info:
```

Running Xubuntu 10.10 using NetworkManager on a WPA protected network
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

Manuel

---

### Post by jonobr on 2012-01-10
Seems to be an [open bug?]("https://bugs.launchpad.net/ubuntu/+source/ieee80211/+bug/889675")

---

### Post by Aqlor on 2012-01-10
Yes, it is an open bug, however, on launchpad there isn't any information about workarounds or a way to get the old packages (if a new package is the cause of the problem). 

That is what I am hoping for by asking here in the forum.

---

