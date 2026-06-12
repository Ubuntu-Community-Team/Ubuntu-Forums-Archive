---
title: "sharing internet network manager"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by ammoun on 2011-01-03
Hello,

I used network manager to share internet connection coming to wlan0 with eth1.

I have internet in my PC coming to wlan0 and I want the client I hook to eth1 to have internet too.

It works with network manager but I think it added something I didn't ask for... Apparently the client connecting to eth1 is recieving an IP from a DHCP server outside the range of wlan0 IPs.

How can I configure eth1 to assign an IP that is inside my wlan0 LAN or at least give a static address to eth1 client that's inside my wlan0 LAN and internet keeps functionning.

Thank you

---

### Post by ammoun on 2011-01-03
wlan0 ip: 192.168.0.101 GW: 192.168.0.4
eth1 ip: 10.42.43.45 GW: 10.42.43.45

Does network manager set a routing function by default? I just wanted a bridge.

---

