---
title: "No all ipv4 packets was sent after SNAT, why?"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by Bi11gates on 2011-02-23
I'm trying to run L2TP/IPsec VPN on Ubuntu 10.04 LTS. And now ppp0 is connected but SNAT is not working well.

When I ping 209.A.A.B through vpn connection, it's OK. But ping 8.8.8.8, timeout.

I logged the POSTROUTING/nat, packets were logged well:
Feb 23 00:55:00 IN= OUT=eth0 SRC=10.1.2.2 DST=209.A.A.B LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=111 PROTO=ICMP TYPE=8 CODE=0 ID=43275 SEQ=0
Feb 23 00:55:07 IN= OUT=eth0 SRC=10.1.2.2 DST=8.8.8.8 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=43876 PROTO=ICMP TYPE=8 CODE=0 ID=43531 SEQ=0

But tcpdump -i eth0, only 209.A.A.B icmp were sent. No packet sending for 8.8.8.8 .

Only ip in same subnet with host 209.A.A.A, like 209.A.A.B, can response the ping, packets will send by eth0.
But other ip, like 8.8.8.8, I can log in iptables POSTROUTING/nat, but no packets sent by eth0 (tcpdump captures nothing).

**ifconfig:**
```
ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.1.2.1  P-t-P:10.1.2.2
eth0      Link encap:Ethernet
          inet addr:209.A.A.A  Bcast:209.A.B.255  Mask:255.255.248.0
[COLOR="Silver"]eth0:0      Link encap:Ethernet
          inet addr:209.A.D.A  Bcast:209.A.D.255  Mask:255.255.255.0[/COLOR]
```

**iptables:**(default all accept)
```
Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
LOG        all  --  10.1.0.0/16          anywhere            LOG level debug prefix `sss '
MASQUERADE  all  --  10.1.0.0/16          anywhere
```

**route**
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.2.2        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
[COLOR="Silver"]209.A.D.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0[/COLOR]
209.A.A.0    0.0.0.0         255.255.248.0   U     0      0        0 eth0
[COLOR="Silver"]0.0.0.0         209.A.D.1    0.0.0.0         UG    100    0        0 eth0[/COLOR]
0.0.0.0         209.A.A.1    0.0.0.0         UG    100    0        0 eth0
```

Resolved**
209.A.D.1 is a bad gateway that massed up route table, due to wrong interface configuration.

---

### Post by Bi11gates on 2011-02-23
ip_conntrack shows:

icmp     1 25 src=10.1.2.2 dst=8.8.8.8 type=8 code=0 id=1293 packets=1 bytes=84 [UNREPLIED] src=8.8.8.8 dst=209.A.A.A type=0 code=0 id=1293 packets=0 bytes=0 mark=0 secmark=0 use=2

icmp     1 4 src=10.1.2.2 dst=209.A.A.B type=8 code=0 id=1037 packets=7 bytes=588 src=209.160.40.4 dst=209.A.A.A type=0 code=0 id=1037 packets=7 bytes=588 mark=0 secmark=0 use=2

OK for 209.A.A.B, but not working for others.

---

### Post by Bi11gates on 2011-02-23
SOLVED!
There is nothing wrong with VPN or iptables.
It's caused by wrong configuration of network interface!

The host provider added a IP alias to eth0, as we requested. But he set a wrong gateway to eth0:0.
So, two default route, good one with eth0, bad one with eth0:0, massed up the route table.

Everything works great if just taking eth0:0 down.

So I edited /etc/network/interfaces, remove bad gateway, restart networking. Done.

---

