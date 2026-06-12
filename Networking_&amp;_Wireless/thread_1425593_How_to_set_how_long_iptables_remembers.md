---
title: "How to set how long iptables remembers?"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by khaan on 2010-03-09
Hi,

I've got a box with 2 interfaces, with IP1 = 192.168.100.1 and IP2 = 10.1.1.1 respectively on them.
I've got an iptables rule that looks like:

```
iptables -t nat -A POSTROUTING -s 192.168.100.0/24 -d 10.0.0.0/8 -p udp -j SNAT --to-source 10.1.1.1 --random
```

If I get 2 consecutive packets from the same address and port from 192.168.100.0/24, they get SNAT-ed and come out of the same port on 10.1.1.1. If then I get another packet from the same address and port 10 minutes later, then it gets SNAT-ed, but comes out of a different port on 10.1.1.1.

My question is: how can I set the time delay I would like iptables to remember its incoming address/port to outgoing port mappings?

---

### Post by Barriehie on 2010-03-09
Nm

---

### Post by khaan on 2010-03-10
SOLVED:

```
sudo sysctl -w net.ipv4.netfilter.ip_conntrack_udp_timeout_stream=600
```
sets the limit within which packets are considered to be in the same UDP stream (and are therefore SNAT-ed from the same port) to 600s.

---

### Post by Barriehie on 2010-03-10
> **khaan said:**
> SOLVED:

```
sudo sysctl -w net.ipv4.netfilter.ip_conntrack_udp_timeout_stream=600
```sets the limit within which packets are considered to be in the same UDP stream (and are therefore SNAT-ed from the same port) to 600s.

Good to know!

---

