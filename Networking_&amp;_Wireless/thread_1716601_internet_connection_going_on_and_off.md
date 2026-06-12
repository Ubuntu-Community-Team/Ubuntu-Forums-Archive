---
title: "internet connection going on and off"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by Omar11 on 2011-03-28
hai, I've been waiting for 30 minutes to get my connection with the modem to stop going on and off (connected/disconnected) Is there any security thing that goes in it (like I'm being hacked or something and I need some more security)or is it the modem and I? Don't send any terminal codes please... I know how they work.
Btw, I use Maverick more than windows.

---

### Post by jmlm-1970 on 2012-10-24
It can be several things:

1. disk hardware failure, like I/O errors, can cause net to go off because it fails to store data from browser.

2. firewall blocking traffic, should have a rule to allow out tcp 25,53,80,110,443 and also allow out udp 53.

3. if you have multiple firewalls programs, running simultaneous, that can also became a problem, like ufw and gufw, it is better to use only gufw...

---

