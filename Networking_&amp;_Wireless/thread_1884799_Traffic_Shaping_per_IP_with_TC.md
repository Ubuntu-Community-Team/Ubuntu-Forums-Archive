---
title: "Traffic Shaping per IP with TC"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by johnny.minty on 2011-11-22
Hello, 

Im trying to shape download speed per IP using TC. I'm having limited sucess with each IP hitting the correct class based on the filter i define however  there is a huge amount of latency & it seems to be shaping the whole interface.

I am trying to shape the following IP's on VLAN 41 and 150 respectively:
10.3.41.90 / 10.3.150.124 

I am using the following TC commands:

tc qdisc del dev eth3.41 root
tc qdisc del dev eth3.150 root

tc qdisc add dev eth3.41 root handle 1 htb default 10
tc class add dev eth3.41 parent 1: classid 1:1 htb rate 100mbit
tc class add dev eth3.41 parent 1: classid 1:10 htb rate 256kbit
tc filter add dev eth3.41 parent 1: protocol ip handle 800::90 prio 1 u32 match ip dst 10.3.41.90


tc qdisc add dev eth3.150 root handle 1 htb default 10
tc class add dev eth3.150 parent 1: classid 1:1 htb rate 100mbit
tc class add dev eth3.150 parent 1: classid 1:10 htb rate 256kbit
tc filter add dev eth3.150 parent 1: protocol ip handle 800::90 prio 1 u32 match ip dst 10.3.150.124


I have attached 2 screens below showing each class working.

My Questions are :

1 ) Does TC handle VLAN interfaces correctly?
2 ) Is there anyway to tune the commands i am using to reduce latency and delay?
3 ) Are the commands i am using applying the filters correctly?






I appreciate any help you can give me,
Cheers
JM

---

