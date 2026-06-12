---
title: "Bonding problem - no load balancing ?"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by qrz73 on 2013-09-05
Hello. I added new 2-port NIC in backup server with Ubuntu 12.04 and try to do bonding with load balancing. I use mode 6, so balance-alb. The bonding itself works ok, but through ifconfig I see that almost all RX traffic goes through one interface. Netstat shows that there are 3 active connections now (these are all another machines that send backups to server).
I thought there must be some sort of load balancing - so, machine1 will use one link and machine2 the second, but it seems it's not. Here's my config, /etc/network/interfaces:
auto eth3
iface eth3 inet manual
bond-master bond0

auto eth2
iface eth2 inet manual
bond-master bond0

auto bond0
iface bond0 inet static
address 192.168.0.1
netmask 255.255.255.0

bond-mode balance-alb
bond-miimon 500
bond-slaves eth2 eth3

And here is /proc/net/bonding/bond0:

Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: eth2
MII Status: up
MII Polling Interval (ms): 500
...
Slave Interface: eth3
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 1
Permanent HW addr: 00:15:17:95:00:df
Slave queue ID: 0

Slave Interface: eth2
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:15:17:95:00:de
Slave queue ID: 0

---

