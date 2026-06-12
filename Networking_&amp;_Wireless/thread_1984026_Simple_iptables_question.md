---
title: "Simple iptables question"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by gear3D on 2012-05-21
Hello,

I have setup a Greasyspoon ICAP server listening on 127.0.0.1:1344 however I want to allow traffic from my LAN eth0 NIC to the loopback port.

Is the best option to:

iptables -A FORWARD -i eth0 -o lo --dport 1344 -j ACCEPT
iptables -A FORWARD -i lo -i eth0 --dport 1344 -j ACCEPT

If you have had experience with Greasyspoon can you confirm that adding this parameter in icapserver.conf will direct Greasyspoon to listen on the specified port?

icap GreasySpoon 192.168.0.1 1344 greasyspoon.ini

Thank you

---

### Post by nikunjmaster on 2012-05-24
Your server is listening on 127.0.0.1 so it will not respond to the traffic coming from eth0.
You can try ssh tunnel.

---

