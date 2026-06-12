---
title: "multiple instance of dhclient"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by rpcarter on 2010-09-13
I have a Lucid 64bit server implementation. I appear to have two versions of dhclient3 running at all times as shown below. I wonder whether this is normal and if not if there is a solution to fix? As can be seen both instances are attached to the same interface i.e. eth0.

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

I noticed this when trying to identify why I get repeated "Sep 13  14:13:56 vmserver dhclient: DHCPREQUEST of n.n.n.n  on eth0 to n.n.n.n  port 67" about every 10 seconds and an explanation of this would also be appreciated.

---

### Post by rpcarter on 2010-09-13
Solved this myself. I am running an LXC container and it would seem the second DHCLIENT is running within this. Lack of experience with LXC but lesson learnt.

---

