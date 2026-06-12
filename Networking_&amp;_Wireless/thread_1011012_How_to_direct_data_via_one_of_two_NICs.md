---
title: "How to direct data via one of two NICs"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by fopetesl on 2008-12-14
I'm running 5.10 Breezy.
I have two NICs one on eth0 with fixed IP 192.168.1.20 which is linked via Ethernet to a local controller.

I also have a Network Gateway via eth1 DHCP which can connect to either a local network or router.

I want to be able to direct commands by choice to one or the other.
e.g. for eth0 with eth1 as the Gateway```
root@AL2ooo~# echo !HH | nc 192.168.1.6 80
~bash: !HH | nc 192.168.1.6 80: event not found
root@AL2ooo~# 
```

However, with eth0 as the Gateway it works as expected and the controller responds accordingly.

How do I over ride the Network Gateway?

Bridging doesn't seem to be the answer and googling hasn't provided any clues.

---

### Post by fopetesl on 2008-12-15
Ummm. This seems to be a difficult one :(

---

