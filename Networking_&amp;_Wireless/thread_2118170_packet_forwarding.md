---
title: "packet forwarding"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by cookie9 on 2013-02-20
hello can somebody tell me how a node decides to which intermidiate node send a packet to arrive at the final destination? i mean if the sender is 5 hops away from the receiver how does it choose the intermidiate nodes?
tnx

---

### Post by iponeverything on 2013-02-20
the routing table.

---

### Post by cookie9 on 2013-02-20
yes but how this table is constructed.. the node knows that has to send that packet to that node because routing table says that but why?

---

### Post by iponeverything on 2013-02-20
the local interfaces have ip addresses and netmasks. 

With just that information, it knows about about locally attached networks.

Anything else is shovelled out the default route where the process is repeated.

---

### Post by iponeverything on 2013-02-20
in the case of border routers - BGP or some other routing protocol - will exchange information about attached and transit networks.

---

### Post by jonobr on 2013-02-20
Hello

Just to add

an interior routing protocol propagates the routes through the network.

There is distance vector protocols like [RIP and RIPV2]("http://en.wikipedia.org/wiki/Routing_Information_Protocol").
The routing table will have a route to a network with the amount of hops involved.

There is a [OSPF]("http://en.wikipedia.org/wiki/Open_Shortest_Path_First") which is a link state protocol. This will take into account the types of links (fiber, ethernet etc)  into the routing calculation as routing over a dialup link would not be as fast as routing over a fiber.

There there are hybrids like [EIGRP.]("http://en.wikipedia.org/wiki/Enhanced_Interior_Gateway_Routing_Protocol")

All of these routing protocols are designed to pass information of the network to routing devices.

There are tonnes of resources out there especially RFC (request for comments) so take a read of those,

---

### Post by cookie9 on 2013-02-21
Ok thank u so much :)

---

