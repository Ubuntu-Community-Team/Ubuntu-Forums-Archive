---
title: "Routing network traffic via a PC to the router"
date: 2012-08-31
forum: Networking &amp; Wireless
---

### Post by apoth on 2012-08-31
I have the following machines:

Router (192.168.0.1)

Intended-gateway (192.168.0.2)

Client (192.168.0.3)

And I'd like to set the default gateway for the client to be the intended-gateway, which has the router as the default gateway.

Any ideas as to what needs to be done to do this? I'm guessing enabling ip forwarding on the intended-gateway and some iptables rules to enable NAT? Thanks in advance.

---

### Post by Bachstelze on 2012-09-01
If you really need all the machines to be on the same network, you will need to enable bridging, not NAT (basically you make intended-gateway act as a switch, not a router).

---

### Post by apoth on 2012-09-01
I'm not after a bridge, I don't think, although granted it may not be NAT.

These machines are already on the same network all using the router as the default gateway. I want to route all the traffic that would normally go straight out via the default gateway via an Ubuntu machine which I can use to sniff the traffic - I can't do this on my router.

---

