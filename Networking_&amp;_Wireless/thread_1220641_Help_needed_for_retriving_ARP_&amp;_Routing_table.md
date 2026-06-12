---
title: "Help needed for retriving ARP &amp; Routing table"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by linuxgroups on 2009-07-23
Hi there,
as part of network audit,i am trying to get ARP & routing table with following commands :KS

#arp -a (this shows me only one line otput)
? (192.168.1.89) at 00:1B:0F:D0:70:BE [ether] on eth0

#netstat -r 
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.1.89    0.0.0.0         UG        0 0          0 eth0



i just want to know, m i doing correct thing:confused:is this output sufficient to submit in network audit report:confused:


Thnks in advance

---

