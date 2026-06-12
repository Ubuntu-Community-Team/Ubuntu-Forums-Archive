---
title: "Can't get BCM4328 working in 8.10"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by BobW on 2008-12-21
I replaced the network card in my Dell laptop with:
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I haven't been able to get it to work properly.

I started with the "wl" driver and it connects to my network, but the performance is terrible. Pinging another machine gives times from 0.2 ms to 500 ms. Browsing the net is painful.

In the syslog I see lots of messages like this:
Dec 21 08:18:09 dell NetworkManager: <debug> [1229869089.365722] periodic_update(): Roamed from BSSID 00:14:D1:C4:4B:43 (My_BSSID) to (none) ((none)) 
Dec 21 08:18:15 dell NetworkManager: <debug> [1229869095.369737] periodic_update(): Roamed from BSSID (none) ((none)) to 00:14:D1:C4:4B:43 (My_BSSID) 

I then tried switching to ndiswrapper. I was able to load the driver and I could see the network in Network Manager, but it would never successfully connect.

I've been going crazy trying to get this working - any suggestions?

---

