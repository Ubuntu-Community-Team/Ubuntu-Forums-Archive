---
title: "How to input IP and DNS etc. for Wifi network"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by penguin5 on 2010-01-15
This may be a dumb question but I honestly do not know where to enter in IP address and all of the fields you would find in windows connection options. Im trying to set up a static IP but I dont even know where to enter the info for my wifi. Thanks.

---

### Post by efflandt on 2010-01-15
At the top of gnome System > Preferences > Network Connections, add a Wireless connection with whatever SSID, wireless security, and ipv4 settings.  Note that when specifying IP, you also need to specify netmask, gateway (typically your router LAN IP), and nameserver(s) (often also your router LAN IP if it handles DNS, unless you use your ISP's nameservers directly).

---

