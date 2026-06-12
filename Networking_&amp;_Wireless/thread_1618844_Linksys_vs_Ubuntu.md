---
title: "Linksys vs Ubuntu"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by ramhanuman on 2010-11-11
I got a Cisco-Linksys E2000 router and have Ubuntu 10.10 on my laptop. I have tried everything i could find but in the end everyone can connect to my router except me and i can connect to everyone else's router except mine. I can see my router and i've tried different security modes like wpa2, wpa, wep, wpa mixed, nothing works. I've tried just using wicd or network manager. Still nothing. Any solutions?

Network card (Broadcom):
1)Ethernet Controller: NetXtreme BCM5755M Gigabit ethernet PCI Express (rev 02)
2) Network Controller: BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by Matti L on 2010-11-11
Try it without security first and then different channels.

---

### Post by ramhanuman on 2010-11-11
Do you know of any settings that work, or do I just have to try every 20-30 different combinations of no secuity with diff channels and security with diff channels? Also my network card is b/g and the router is set to mixed (b/g/n) but there is a setting for only b/g, would that help?

---

### Post by ramhanuman on 2010-11-11
nothing?

---

### Post by Matti L on 2010-11-12
Sorry for not replying sooner but I was busy. I have a Linksys WRT54G with these settings:
Wireless Network Mode: Mixed (B/G)
Wireless Channel: 11 - 2.462GHz
Wireless SSID Broadcast: Enable
Security Mode: WPA2 Personal
WPA Algorithms: TKIP+AES

I had trouble getting Ubuntu to use my wireless too (no problems in Vista) until I found those settings to work but that was year or two ago and haven't tried other settings with new Ubuntu releases (if it works why change it?).

That's all the help I can give you so hopefully someone else knows better.

---

