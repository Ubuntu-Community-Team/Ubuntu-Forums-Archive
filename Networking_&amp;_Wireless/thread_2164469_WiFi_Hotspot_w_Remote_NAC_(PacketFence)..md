---
title: "WiFi Hotspot w/ Remote NAC (PacketFence)."
date: 2013-07-31
forum: Networking &amp; Wireless
---

### Post by WittyDBlack on 2013-07-31
What I'm trying to accomplish is the capability to allow or deny access to a WiFi hotspot, remotely. At the moment, my ubuntu server is local (connected to the router that has internet access). I have a VPS but I'm not entirely sure how to go about configuring it. I'm no stranger to software engineering but I've just started getting in-depth with networking so I'm not completely sure of which technologies I'd need or if what I'm trying to do is possible.
The network configuration that I had in mind consists of a cable modem(with internet access) connected to a router (with dd-wrt firmware) which then broadcasts some arbitrary SSID. Clients would then connect to the router wirelessly then somehow be routed to my VPS which accepts or denies access to the internet (?).
Authorization is the only aspect that I'm interested in my VPS doing because of bandwidth restrictions. If it's possible to allow a client to use the local routers access to the internet once access has been granted by my VPS then that would be great (and cheaper).

My VPS is running Ubuntu 12.04 has one interface and the NAC that I've been using is called PacketFence (which is installed but not configured). Please let me know if more information is needed about the modem, router, or server.

Any help is greatly appreciated! Thanks in advance.

---

