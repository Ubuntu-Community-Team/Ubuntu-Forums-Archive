---
title: "Using a server as an AP"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by Jophish on 2009-09-19
I have set up a server running karmic Alpha 6.
I have got the wlan0 in master mode, and is broadcasting a wireless network, I used Hostapd to do this.
It is connected to my network via eth0 and has ip 192.168.0.3.

I have tried to set up a bridge between the two however, although I think that the br0 is set up correctly. When I connect to the wireless network, I can't get an ip from 192.168.0.1 with dhcp. I can only connect to the wireless network with a static ip. however when I do this, the only machine I can ping is myself, not even the server (I can't determine its ip address on the wireless network. ifconfig on the server produces a ipv6 ip) nslookup localhost on the laptop times out, "no servers could be reached"

What I want to do is set up a bridge between wlan0 and eth0 on the server, so any device connecting to the wireless network acts as if it is connecting straight to the wired network through a regular AP.

Thanks

Joe

---

