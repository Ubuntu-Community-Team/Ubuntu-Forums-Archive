---
title: "Enable Generic Routing Encapsulation through Gateway"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by cleanroom on 2009-09-09
Hello,
   I have a 6.06 server acting as a gateway and I am trying to connect to a VPN account through the gateway but having no luck.  The techs at the VPN account tell me I need to enable Generic Routing Encapsulation on my gateway, but I have not been able to find any info on how to do that in Ubuntu.

Any ideas?

---

### Post by cleanroom on 2009-09-11
Ok so since no one has given me any ideas.  I added these lines in my iptables script.

$IPTABLES -A FORWARD -p 47 --src xxx.xxx.xxx.xxx -j ACCEPT
$IPTABLES -t nat -A PREROUTING -p 47 -j DNAT --to 192.168.1.1

However, it still doesn't work.

---

