---
title: "IPv6 native networking setup"
date: 2012-09-05
forum: Networking &amp; Wireless
---

### Post by MadEgg on 2012-09-05
I have a server running Ubuntu 10.04 in a datacenter. It was set up for IPv4 and all works fine.

My ISP there started to offer IPv6 connectivity so I decided to give it a shot. I got a /96 subnet, and (something like) the following info:

```

ip range: 2aaa:bb:cc:dd:ee:ff:xxxx:xxxx/64
gateway: 2aaa:bb:cc:dd:ee::1
dns: 2aaa:bb::10:20

```

where xxxx: xxxx can be anything from 0000: 0000 to ffff: ffff

So, I decided to start of with 0000:0001, and added this to my /etc/network/interfaces:

```

iface eth0 inet6 static
    address 2aaa:bb:cc:dd:ee:ff::1
    netmask 64
    gateway 2aaa:bb:cc:dd::1
    dns-nameservers 2aaa:bb::10:20

```

After I did this, and reloaded the network settings the settings seemed to be fine.

ip -6 addr shows (something like) this:

```

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 2aaa:bb:cc:dd:ee::1/64 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::aa:bb:cc:dd/64 scope link 
       valid_lft forever preferred_lft forever

```

route -6 shows (something like) this:

```

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2aaa:bb:cc:dd::/64           ::                         U    256 0     1 eth0
fe80::/64                      ::                         U    256 0     0 eth0
::/0                           2aaa:bb:cc:dd::1         UG   1   0     9 eth0

```

So, all seems to be allright. I then found out I had to set IPV6=YES in /etc/default/ufw to stop ufw from blocking all IPv6 traffic. Now, I can ping my own IPv6 address:

```

$ ping 2aaa:bb:cc:dd:ee:ff::1
PING 2aaa:bb:cc:dd:ee:ff::1(2aaa:bb:cc:dd:ee:ff::1) 56 data bytes
64 bytes from 2aaa:bb:cc:dd:ee:ff::1: icmp_seq=1 ttl=64 time=0.064 ms
64 bytes from 2aaa:bb:cc:dd:ee:ff::1: icmp_seq=2 ttl=64 time=0.039 ms

```

The gateway is unpingable though:
```

$ ping 2aaa:bb:cc:dd::1
PING 2aaa:bb:cc:dd::1(2aaa:bb:cc:dd::1) 56 data bytes
From 2aaa:bb:cc:dd:ee:ff::1 icmp_seq=1 Destination unreachable: Address unreachable
From 2aaa:bb:cc:dd:ee:ff::1 icmp_seq=2 Destination unreachable: Address unreachable
From 2aaa:bb:cc:dd:ee:ff::1 icmp_seq=3 Destination unreachable: Address unreachable

```

What am I doing wrong? Are there other settings I need to enable / change / disable?

---

### Post by lemming465 on 2012-09-05
Um, maybe try *ping6* instead of ping?

---

### Post by MadEgg on 2012-09-06
UGggh, stupid typo. I used ping6 instead of ping of course; still doesn't work.

---

### Post by lemming465 on 2012-09-07
What does rdisc6 show in the way of router advertisements on the LAN?

---

### Post by MadEgg on 2012-09-07
```

$ rdisc6 eth0
Soliciting ff02::2 (ff02::2) on eth0...
Timed out.
Timed out.
Timed out.
No response.

```

---

### Post by MadEgg on 2012-09-07
Hmm, the lack of routers adverterising got me seriously doubting the IPv6 setup of my ISP so I contacted them. Apparently, one of their routing tables had been misconfigured so I couldn't reach the router. They fixed this and now it's working.

Thanks for the help!

---

