---
title: "Need help with getting internet connection through router switch"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by miker95 on 2013-01-26
Hello, I've been using Ubuntu Server 12.04, upgrading to 12.10 once I figure this out, on my IBM xSeries 335 (name: Server1; ip: 10.0.0.50) as a web server. I recently got a computer from a family friend that I want to set up as a file server (name: Server2; ip: 10.0.0.51). I won't be able to get an actual network switch for a while so I've decided to use an old router as a switch. 

I disabled the router firewall, DHCP server, and Public LAN. This all works on my regular desktop, I can plug the switch to my router then switch to my PC and I get internet connection. But when I take the switch to my basement, both Server1 and Server2 don't receive an internet connection. I've tried changing resolv.conf, and /etc/network/interfaces. Changing neither works. I can't even ping my computer, 10.0.0.8, or the router, 10.0.0.1.

What am I doing wrong? Why don't my servers receive a LAN connection or an internet connection? Please help this is driving me insane.

Alternatively I've tried multiple times to set up Server1 (3 NICs) with internet sharing to Server2 (1 NIC). I've tried several online tutorials on how to do this, and none have worked. I don't want to try internet sharing anymore.

Just to be double clear, what is desired:
[IMG]http://s13.postimage.org/96xa4pqt3/Untitled_1.png[/IMG]

---

