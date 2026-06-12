---
title: "Multi-homed box (no routing, no balancing)"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by jaofos on 2011-04-11
I am trying to setup a multi-homed network in a Ubuntu 10.10 environment.  I have eth0 which covers an internal, private network via Ethernet, and accepts inbound connections (web server, etc).  I have a wireless connection on eth1 which I want to be the only connection our to the internet.  I would also like a squid proxy setup to listen to inbound connections on the wired LAN, but request internet pages via the wireless LAN.  Note that I do not wish to route between the two networks outside of Squid.  The network traffic should remain as isolated as possible on the two LAN's.

I have it sort of working, squid works, outbound connections work, but there is a significant delay on any network requests in and out of the box.  I'm sure I need to optimize my routing somehow, and any tips to do so or links to articles which cover this would be greatly appreciated.

---

