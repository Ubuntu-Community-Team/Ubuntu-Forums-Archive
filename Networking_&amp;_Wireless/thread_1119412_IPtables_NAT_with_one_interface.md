---
title: "IPtables NAT with one interface"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by robTard on 2009-04-07
Hello,

I am trying to create a NAT on a machine using IPTables that has only a single physical interface (wireless atheros chipset).  I would like to have
several different clients connect to this machine essentially as a proxy, but since it needs to keep track of different clients they need to be NAT'd.

Thanks

---

### Post by lensman3 on 2009-04-07
NAT doesn't make much/any sense on a machine that only has one interface.  

You really need two interfaces.  If the clients, in your case, are coming into your machine on the wireless and then the packets get forwarded to a Ethernet card, then NAT makes sense.  One interface card, but with two networks on the one wire could use NAT.  The packets would be forwarded to another IP address range.  Yes one Ehternet wire can have to IP ranges and numbers.  Actually works quite well.

The proxy's are going to have to forward the packets to the default gateway using the routing table.  Look at the "route" command.  I don't think you want NAT in this case.  The proxys should be on the default gateway for your network.

---

