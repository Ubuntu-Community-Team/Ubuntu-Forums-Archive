---
title: "Weird RAW sockets and iptables issue…"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by skypemesm on 2010-10-18
Not sure if this is the right place to ask, but here is my question:
        I am trying to redirect all incoming traffic on UDP port 5060 to port 56790, and all outgoing traffic from 5060 to the port 56789. I used these iptables rules:

iptables -t nat -I PREROUTING -p udp ! -s localhost --dport 5060 -j REDIRECT --to-port 56790
iptables -t nat -I OUTPUT -p udp ! -s localhost --sport 5060 -j REDIRECT --to-port 56789

I listen on both ports using RAW SOCKETS after setting the interface to PROMISCUOUS mode using ioctl.

I see packets ONLY on 56789 i.e.SENDING side, and I do not see any packets on 56790, while wireshark shows that many packets are delivered to port 5060.

Why would this happen? Any ideas? Do you think it's a problem with iptables rules or something to do with raw sockets?

---

