---
title: "WEP HEX with gnome network manager"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by ignition1987 on 2010-04-08
Hi guys,

This morning I had kind of a panic attack when Wicd asked for my password to access the network devices. It had never done this before but skeptically I entered my password... only to see wicd exit right after that. Starting it again from Applications had no effect. Reinstalling gnome network manager was difficult without internet but dhclient eth0 luckily did work so I managed to get gnome network manager back on it. But that lead to whole reason why I switched to wicd in the first place: I simply can not get gnome network manager to connect to WEP using the hex key, even tho the exact same key works perfectly with wicd.

I guess this leaves me with 2 choices:

1. use gnome network manager without HEX WEP
2. use wicd but live with the fact it might suddenly **** up, and I don't always have a wired network to fix the damn thing

Any input would be appreciated. I would prefer getting HEX WEP to work with the gnome network manager...

---

### Post by inobe on 2010-04-08
try reseting the modem and the router by unplugging them, let the first device assign a new ip before starting the router.

also in network manager' never mess with the settings, if it's set for wpa whatever' just continue to apply the wep key anyway.

---

### Post by ignition1987 on 2010-04-08
It is officially not my network so I am not at liberty to reset the modem. Still I don't see why this is relevant... Since it works with wicd and not with gnome network manager it must clearly be a software problem with gnm. Also gnm detects the right setting (WEP 40bit/128bit Key) but clearly it does not apply it properly.

---

### Post by ignition1987 on 2010-04-08
Doh, adding backtrack repositories to ubuntu was such a bad idea. It installed gnm 0.7, updating to the latest version (0.8) solved everything. This can be closed.

---

