---
title: "ipv6 route problem......"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by dashang.trivedi on 2011-09-06
my ubuntu machin 1) 2000:470:1f01:115::3/64 is connect to switch ...

one more server machine connect to switch at eth5 : 2000:470:1f01:115::4/64

now in that server machine eth7 ip : 2001:470:1f01:115::7/64
one other machine connect with eth7 ip is 2001:470:1f01:115::8/64....

ubuntu machine  to server eth5 ping6 is success full
eth5 to server machine eth5 ping6 is success full
eth5 to eth7 ping6 is success full
eth7 to eth5 ping6 is success full

now from ubuntu machine 2000:470:1f01:115::3/64 to eth7 ip : 2001:470:1f01:115::7/64 ping6 is not success full ..

Problem is Route because of range 2000 and 2001....
i dont know how to add route of ipv6 and in which machine i have to add route....???

please suggest me....

---

