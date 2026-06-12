---
title: "ifup problem: DHCPDISCOVER requests going to 255.255.255.255"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by TeeAhr1 on 2008-12-03
Okay, I'm at a loss here. When trying to use ifup or dhclient, I always hang at:

DHCPREQUEST from wlan0 to 255.255.255 port 67 interval 6
DHCPREQUEST from wlan0 to 255.255.255 port 67 interval 11
etc.

Obviously the problem is that my DHCP server is my modem, which is 192.168.0.1. But in three days of searching, I have been unable to figure out how to get my machine to go there. I should add that the card works fine, Network Manager works fine, etc. I'm trying to figure this out for when I'm using Fluxbox. Any guidance would be much appreciated.

best-
p.

---

