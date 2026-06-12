---
title: "Application/ Network Mapping Ideas"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by Shaker242 on 2010-01-22
I have an application routing complication that I'm looking for some direction with.  This is to help an application's interaction with multiple components, but I will try to discribe it as clear as possible.  Again, this is not a user issue so for testing purposes this is basic.

Setup:
One server (SVR1) with two interfaces and 5 subs - 
eth0 172.16.0.18
    default gatway 172.16.0.1

eth1 192.168.0.254
    eth1:1 192.168.0.1
    eth1:2 192.168.0.2
    eth1:3 192.168.0.3
    eth1:4 192.168.0.4
    eth1:5 192.168.0.5


Second server (SVR2 - for testing) running Apache 0.0.0.0:80
eth0 172.16.0.17
    default  gateway 172.16.0.1

eth1 192.168.0.100

Objective:
While on server SVR1, I would like to make a connection to SVR2 via 192.168.0.100:80; however, I would like the source IP's to rotate through the 5 subs.

Example:
While on SVR1 I telnet to SVR2:80 and fetch the default page, and the Apache2 access.log on SVR2 shows 192.168.0.1 (the first attempt), .2 (the second), .3 (the third), etc.

I was thinking of iptables using some natting, or LVS or even Squid... but I'm really not sure if it's possible with any of these.  Thoughts?

---

