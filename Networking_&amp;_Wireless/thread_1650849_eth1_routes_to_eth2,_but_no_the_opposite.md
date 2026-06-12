---
title: "eth1 routes to eth2, but no the opposite"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by fdelval on 2010-12-22
Hello, check the ttached file.


I have a host in 192.168.3.x and another in 192.168.4.x

Both conect to same server with 2 interfaces ending in .254


I have no iptables rules, i activated /proc/sys/net/ipv4/ipv4_forwarding to 1


The host 192.168.3.3 can ping 192.168.3.254 but not 192.168.4.254
The host 192.168.4.4 can ping 192.168.3.254 and can ping 192.168.4.254


Why?

---

### Post by fdelval on 2010-12-22
i just thought if i could check the logs?   syslog?
*im on debian


route table has:

192.168.4.0........0.0.0.0...........255.255.255.0.... u .... 0 ..... 0 .... eth1
192.168.3.0........0.0.0.0...........255.255.255.0.... u .... 0 ..... 0 .... eth0
0.0.0.0 ........ 192.168.3.1...........0.0.0.0.... ug .... 0 ..... 0 .... eth0


client PC's are windows with no changes at all, and i even tryed to change them, and put each one in the other network.. same result.

---

### Post by Eaglebird on 2010-12-22
Are your subnet masks the same on each machine?

---

### Post by fdelval on 2010-12-22
Hello!,

yes, 255.255.255.0

My guess is that problem is inside the server, not the clients; i can switch the clients and still get same weird problems

---

### Post by fdelval on 2010-12-22
bumpy

---

### Post by KiLaHuRtZ on 2010-12-24
What are your default gateways on the client machines setup for?

Are you attempting to get network "4" to route across the server and egress out via network "3"?

A full topology and interface configs for all machines would be helpful.

---

