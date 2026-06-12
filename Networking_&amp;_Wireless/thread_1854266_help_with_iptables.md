---
title: "help with iptables"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by abulmagd on 2011-10-04
My ISP forwards all ougoing  requests to port 53 to thier own DNS servers, i want to use opendns servers which luckily listen to 5353 port, BSD systems in thier resolv.conf accept

nameserver [208.67.222.222]:5353

tried this on ubuntu 11.04 but didn't work, so i was thinking of port redircting my dns requests to port 5353 

iptables -t nat -A PREROUTING -i eth1 -p udp --dport 53 -j REDIRECT --to-port 5353

this doesn't work to, help is appreciated

---

### Post by SeijiSensei on 2011-10-04
Try replacing "-j REDIRECT --to-port 5353" with "-j DNAT --to-destination 208.67.222.222:5353".  REDIRECT sends the packets to a port on the local machine.  DNAT should send the requests to the remote server's port 5353.

---

### Post by abulmagd on 2011-10-04
didn't work in PREROUTING chain, yet it did in OUTPUT

iptables -t nat -A OUTPUT  -p udp --dport 53 -j DNAT --to-destination :5353

---

