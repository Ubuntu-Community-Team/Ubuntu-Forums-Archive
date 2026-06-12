---
title: "UDP not being forwarded via GRE tunnel"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by westingham on 2013-08-28
Let me start off by saying that I followed this guide: [http://wiki.buyvm.net/doku.php/gre_tunnel](http://wiki.buyvm.net/doku.php/gre_tunnel)

Once it's all setup, I'm able to ping the 192.168.168.0/30 networks on both sides and receive a response. I followed all of the iptables setup to the letter except I forwarded UDP port 7777 instead of TCP port 25565.

Attempting to connect to the filtered IP address with my client did not work. I ran tcpdump on the filtered IP address and received the following:

```

22:03:24.500135 IP a.b.c.d > filtered.ip.address.7777: UDP, length 11
22:03:24.500167 IP filtered.ip.address > a.b.c.d: ICMP filtered.ip.address udp port 7777 unreachable, length 47

```

Here is how my iptables are setup:

```

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             filtered.ip.address   udp dpt:7777 to:192.168.168.2:7777

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
SNAT       all  --  192.168.168.0/30     anywhere             to:filtered.ip.address

```
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             192.168.168.2        udp dpt:7777 state NEW,RELATED,ESTABLISHED

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

As near as I can tell, the machine with the filtered IP address should not state that port 7777 is unreachable, but it does.

Any suggestions/ideas?

Edit: Also, for some unknown reason, the tunnel will stop working for a little bit and then start up again.

---

### Post by westingham on 2013-08-28
Bumping for great justice and every zig.

---

