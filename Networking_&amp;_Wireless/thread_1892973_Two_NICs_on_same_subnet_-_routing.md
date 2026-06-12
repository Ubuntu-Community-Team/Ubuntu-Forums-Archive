---
title: "Two NICs on same subnet - routing"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by Mixa84 on 2011-12-09
I have two routers that have LAN IPs 192.168.1.1 and 192.168.1.2. One machine is connected to both routers, eth0 IP 192.168.1.10 -> 192.168.1.1 and eth1 IP 192.168.1.20 -> 192.168.1.2.

I need to configure policy routing to be able to access both IPs (10 and 20) from both routers. I have done this config now so far:

added two lines to /etc/iproute2/rt_tables:
  200 table1
  201 table2

And then set up the routing for those tables.

ip route add 192.168.1.0/24 dev eth0 table table1
ip route add default via 192.168.1.1 table table1
ip route add 192.168.1.0/24 dev eth1 table table2
ip route add default via 192.168.1.2 table table2
ip rule add to 192.168.1.1 table table1
ip rule add to 192.168.1.2 table table2


I`m able to ping every IP from both routers and machine.
I have on Router1 port 24 forwarded to 192.168.1.10 port 22, and on Router2 port 24 forwarded to 192.168.1.20 port 22 but I`m not able to access it.
When I add default route for example: route add default gw 192.168.1.1 dev eth0 , I`m able to access from router1 but not from router2.
I have also tried to do this:
ip route add default scope global nexthop via 192.168.1.1 dev eth0 weight 1 nexthop via 192.168.1.2 dev eth1 weight 1, and then I get to the part to enter the password for ssh but then it freezes.

---

### Post by Mixa84 on 2011-12-12
Anybody?

---

### Post by jonobr on 2011-12-12
I would try and help but am not familiar with using 
iproute2 and rt_tables, i figure I need to study this.
 
From a networking perspective it appears you have to routes defined out two different interfaces to the same subnet, so if I wanted to go to the 192.168.1.x network, your definition seems to have two possibilities and interfaces defined. 

When you add a default route for 192.168.1.1 then anything in the 192.168.1.x range will use that. including 192.168.1.2

However, as said, maybe iproute2 sorts this and using the tables command allows this to be done, but again, from a strict networking angel if you were to do this all your traffic would use one interface.

---

