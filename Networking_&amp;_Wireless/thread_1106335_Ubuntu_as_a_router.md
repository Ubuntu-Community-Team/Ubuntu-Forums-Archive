---
title: "Ubuntu as a router"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by mcstech on 2009-03-25
I need some help. I have to Cisco ASA firewalls that will be used to form a point-to-point VPN. I need to configure them to work at my office, as one of the two end-points will be sent to another state.

The problem is that to set up the ASAs to "talk" to one another, I need to have a router between them. And...I don't have one. But I do have a server, with Ubuntu installed, and two NICs.

My thought is to have each interface act as gateways for the ASAs, and that the server can route between the NICs.

ASA01-->ETH0<-->UBUNTU<-->ETH1<--ASA02

If that makes sense.

ASA01 WAN Info:
IP 192.168.10.90 /30
GW 192.168.10.89

ASA02 WAN Info:
IP 192.168.9.78 /30
GW 192.168.9.77

I set routes from .9.x to ETH0; and from .10.x to ETH1. But no traffic crosses the interfaces.

Help would be appreciated

---

### Post by Iowan on 2009-03-25
Perhaps you've already seen these, but [here]("https://help.ubuntu.com/community/Router") is a help page for Ubuntu router... and [this]("https://help.ubuntu.com/community/SSH_VPN") is a help page for SSH VPN.

---

