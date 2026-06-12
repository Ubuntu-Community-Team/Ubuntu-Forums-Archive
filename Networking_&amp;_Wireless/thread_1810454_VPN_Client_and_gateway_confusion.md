---
title: "VPN Client and gateway confusion"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by joes3029 on 2011-07-23
I've been playing with Ubuntu 11.04, and have been very happy with it, except for one small concern - I have network manager set up to automatically connect to a 3G connection, which is does nicely, and have found the nmcli tool to also make network manager connect to my VPN connection. However, once the VPN connection is established, I cannot access my VPN server at all - even pings are rejected. 

My first guess is a gateway/routing issue, but am finding network manager puts things in different places to my last bit of experience with OpenBSD. Given that I just want calls to 10.8.0.1 (my VPN server) to go out through my OpenVPN connection, and everything else to be routed by 3G, where should I be looking? My attempts to specify routes in the OpenVPN settings in network Manager have not helped.

---

