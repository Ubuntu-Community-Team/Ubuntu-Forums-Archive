---
title: "iptables help"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by amauk on 2009-11-27
Hey all,

iptables is doing my head in, and I'm wondering if anyone can help?

I've setup a VPN connection, interface "ppp0"
and I'm trying to configure my system to send specific packets through "ppp0", with anything else going through "eth0"

I'm wanting outgoing tcp packets with a destination port listed in /etc/ppp/vpn_proxy-ports to go through "ppp0"
Also, communication between me and any domain name listed in /etc/ppp/vpn_proxy-domains to go through "ppp0"

has anyone done anything like this?
Ta

---

