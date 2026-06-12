---
title: "IP packet duplication out multiple interfaces"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by fstab on 2010-04-12
Hi All,

Suppose you have a computer with 3 Ethernet network interfaces and each has a separate physical connection to a distinct subnet.

ie: 
(LAN type interface)
eth0 <--> 192.168.1.1/24

(Two WAN type interfaces)
eth1 <--> 172.16.1.1/20
eth2 <--> 10.1.1.1/24

Now suppose that you want to capture IP packets coming into a given TCP/IP port on the eth0 interface and then send those packets simultaneously out both eth1 and eth2.

It's not standard routing because it involves duplicating the original packet but assume that the application receiving the packets at the final destination handles duplicates are re-ordering based on the payload.

Does anyone know of a way to do this using the kernel or linux tools already available?

Thx.

---

