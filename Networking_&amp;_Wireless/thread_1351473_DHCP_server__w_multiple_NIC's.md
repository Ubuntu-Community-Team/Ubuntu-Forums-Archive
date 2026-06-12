---
title: "DHCP server  w/ multiple NIC's"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by natbob1 on 2009-12-10
I have a server which I would like to configure to act a a DHCP server to some client computers. It has two NIC's.  One is connected to a router which acts as a DHCP server for my LAN. The other is connected to a switch that will connect to the client computer. It is not possible to just directly connect the clients to my router. How would I configure dhcp3-server so that the server would get an IP from the router on eth0 and serve on eth1? When I installed dhcp3 before it didn't get an IP from the router which rendered it unreachable.

Thank You
natbob1

---

### Post by puppywhacker on 2009-12-10
You have to set a static ip-address on the interface you want to have your dhcpd server run on for instance 192.168.0.1 ... Then you define a subnet section in the /etc/dhcp3/dhcpd.conf

something like this will then attach the dhcpd server only on the interface in the same subnet, it will handout ip-address from 192.168.0.40
```
subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.0.1;
        range 192.168.0.40 192.168.0.99;
}
```

---

