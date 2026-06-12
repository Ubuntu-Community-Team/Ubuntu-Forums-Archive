---
title: "Forward all packets from all ports IPTABLES"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by Blackdragon1400 on 2013-08-10
I have looked around for this for a long time and cannot find a good answer. I want to take all the incoming traffic from Machine A on every port and forward it to Machine B where I am running an IDS. All the examples that I can find are for specific ports ie.

**iptables -t nat -A PREROUTING -i eth0 -p tcp --dport $srcPortNumber -j REDIRECT --to-port $dstPortNumber**

Does anyone know how to do this? It would be nice if it used masquarade so I could know that traffic came from Machine A instead of my IDS just seeing it all from Machine B as a destination, but I am not sure how to set it up.

Thanks for the help.

---

### Post by Blackdragon1400 on 2013-08-10
This is very close, but I would like Machine B to know that the packets were meant for Machine A in the first place and for them to go to the same relative port on Machine B:

[B]iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 1:65535 -j DNAT --to-destination 192.168.1.10:10000
[/B]

---

