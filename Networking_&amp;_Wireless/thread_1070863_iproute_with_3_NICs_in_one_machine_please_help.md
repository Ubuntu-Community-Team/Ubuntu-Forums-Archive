---
title: "iproute with 3 NICs in one machine please help"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by Thasp on 2009-02-15
The script I used was as follows. 

```
ip route del default dev eth0
ip route del default dev eth1
ip route del default dev eth2
ip route del table 2
ip route del table 3
ip route add table 2 to default via 10.10.13.1 dev eth2
ip rule add from 10.10.13.25 table 2
ip route add table 3 to default via 192.168.1.1 dev eth1
ip rule add from 192.168.1.5 table 3

ip route add default via 10.10.10.1 dev eth0
```

eth0 is an NIC with an IP of 10.10.10.2 going through 10.10.10.1. 

eth1 is an NIC with an IP of 192.168.1.5 going through 192.168.1.1. 

eth2 is an NIC with an IP of 10.10.13.25 going through 10.10.13.1

If I use all three connections to send files to site A, they will all work perfectly.

However, if I try to download files from site a to eth0, site b to eth1, and site c to eth2, they won't all work. It will give preference to the listing in table2, and table 3's NIC will not show any traffic on nload.  If eth1 ever DOES show traffic, it's because eth2 temporarily had an immediate speed drop. eth0 is not effected by this silliness.

I would like to be able to have files from site A go to eth0, site B go to eth1, and site C go to eth2, all at the same time, with each site using the full bandwidth the NIC is alloted to has to offer. I don't want the one in table 2 to work and in table 3 to not work. This script worked when there were only 2 NICs in the machine, however, now with an added T1, I need it to be scalable over 3 connections.

Here is my current routing table.

> ~# ip r s
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.5
10.10.13.0/24 dev eth2 proto kernel  scope link  src 10.10.13.25
10.10.10.0/24 dev eth0  proto kernel  scope link  src 10.10.10.2
default via 10.10.10.1 dev eth0


Thank you in advance for any help you can provide.

---

