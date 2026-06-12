---
title: "Get IP Address Behind NAT"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by agrd_sn on 2010-04-07
i want to get IP Address of users behind NAT..(192.x.x.x)
is it possible?

the topology:
wireless AP using NAT (192.x.x.x) => Local Area Network (172.x.x.x) => Internet

thx b4,
agrd_sn

---

### Post by chili555 on 2010-04-07
Here is a quick and dirty way to do it:> $ fping -g 192.168.1.100 192.168.1.125
192.168.1.108 is alive
192.168.1.117 is alive
192.168.1.118 is alive
ICMP Host Unreachable from 192.168.1.108 for ICMP Echo sent to 192.168.1.100
ICMP Host Unreachable from 192.168.1.108 for ICMP Echo sent to 192.168.1.100
ICMP Host Unreachable from 192.168.1.108 for ICMP Echo sent to 192.168.1.100
ICMP Host Unreachable from 192.168.1.108 for ICMP Echo
--- snip ---

---

### Post by agrd_sn on 2010-04-07
hi chili555,

i'll try tomorrow.
thx.

---

