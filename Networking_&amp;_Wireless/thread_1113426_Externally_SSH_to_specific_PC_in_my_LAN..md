---
title: "Externally SSH to specific PC in my LAN."
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by Surreal Killa on 2009-04-01
Let's say my IP address is *x.x.x.x* and I have multiple computers going through a router, so they each get an IP address like: *y.y.y.1* and *y.y.y.2*, etc, and I can successfully SSH into any of them from within my local network, how would I do it from outside the network? I haven't tried it yet, but I'm assuming if I tried to SSH to *x.x.x.x* it would try to take me to my router (which obviously wouldn't work).

---

### Post by Huufarted on 2009-04-01
The router is a single IP address.  To connect to an internal PC, you need to tell your router how to forward a port.

Port forwarding is like this.  The router says "I have a connection coming in from the outside on port 80 (http)."  It looks it up and says "Ok, this tells me any inbound connections on 80 need to go to 192.168.1.1"  And it forwards it there.  So, assuming your PCs with SSH all have SSH listening on the same port (22), then you'd forward the port to a different port in addition to the IP.

So a connection coming into the external IP of 11.12.13.14 on port 1022 can be configured to route internally to the IP 192.168.1.1 on port 22.  If a connection gets established instead on port 1023, you can tell the router to forward it to 192.168.1.2 on port 22.

This will allow all of your external connections coming in to be able to be properly routed to the appropriate internal IP address.

---

### Post by Surreal Killa on 2009-04-01
Cool. Thanks. I'll try that.

---

