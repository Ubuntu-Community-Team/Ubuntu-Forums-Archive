---
title: "Iptables with ip_queue and two ethernet"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by stone[no] on 2009-09-10
I'm using iptables with ip_queue to send all incoming traffic on eth0 to honeytrap (a mallware collector)
```
iptables -A INPUT -i eth0 -p tcp --syn -m state --state NEW -j QUEUE
```

I'm using eth1 to connect to my local lan (DHCP) and it is the gateway.
Eth0 has a static IP on the same network and is the DMZ (gets all incoming internet traffic). 
No firewall is active.

When both interfaces are up Ubuntu blocks all incoming traffic to eth0, except port 5900 (remote desktop) (and it seems to be "picked" up by Ubuntu as if it was come from eth1).

How can I use both interfaces and let traffic for eth0 be passed by iptables?

---

