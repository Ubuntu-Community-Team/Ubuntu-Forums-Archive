---
title: "Strange Ubuntu 11.04 wifi connection problem"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by santanafe on 2011-05-12
Using a Thinkpad X60, 32bit Ubuntu 11.04 netinstall.

I'm using nm-applet and wireless networks are visible, and I can click  on them, but nothing happens. cnetworkmanager is the same,  "cnetworkmanager -C <wirelessnetworkname> <etc.>" yields no  error, but no connection is found.

I've used "sudo ifconfig wlan0 up", but that hasn't gotten me any  further. The only anomaly I've found is that I'm getting this  ([https://bugs.launchpad.net/ubuntu/+source/cnetworkmanager/+bug/735532](https://bugs.launchpad.net/ubuntu/+source/cnetworkmanager/+bug/735532))  bug. Are there other wireless settings I need to fiddle with to get the  hardware "up", or "on"? "cnetworkmanager -d" just gives me "wlan0 |  WIRELESS | DISCONNECTED".

Note: the wireless networks are working, and the laptop was working fine using nm-applet on 10.04 earlier today.

---

