---
title: "ip route // source routing policies not (!)always(!) working"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by adieb on 2009-03-11
Hello,

we use a Maschine with 3 NIC to offer dhcp to two different networks. a third NIC is in a seperate network for maintainance.
The DHCP Server needs this source-routing, which means, that received dhcp-requests will be answered through the same interface they came in. (until they don´t have any ip information yet)

So I setted up the rt_tables:
```
echo "100 route115" >> /etc/iproute2/rt_tables 
echo "101 route56" >> /etc/iproute2/rt_tables 
echo „102 route46“ >> /etc/iproute2/rt_tables
```

And for each interface in /etc/network/interface i added some post-up script:
```
auto eth0 
iface eth0 inet static 
	address 131.220.115.37 
	netmask	255.255.255.240 
	network 131.220.115.32 
	broadcast 131.220.115.47 
	post-up /etc/network/if-up.d/jura_src_routing115.sh 

```


Inside this script:
```
#!/bin/sh 
ip rule add from 131.220.115.37 table route115 
ip route add default via 131.220.115.46 dev eth0 table route115 
ip route flush cache 
```

It defines the gateway for that specific network and tells to use it for this NIC.

The same for all other NIC. And fine! It works like this.
But when I restart the VM it might be, that it just works for one or two interfaces.
After restarting the network (/etc/init.d/networking restart) maybe it works on different combinations (nic1 and nic3; or nic1 and nic2).

```
ip route
``` shows no differences.

- "Works" means for me, that I can ping adresses in the same subnet.
- The Maschine is a virtual Maschine running on a Ubunt Host with Virtualbox. I wasn´t sure if it is VirtualBox bug, but it doesn´t seam so, because it is possible to run dhcpclient on a "non-working" NIC, and it can send and receive....

Does anybody have an idea how it is possible, that something works sometimes and sometimes not without any changes in the config?????

I´d really appreciate any ideas... I am struggling with this stupid problem since month and I can not find any solution else then try, try try....

---

### Post by adieb on 2009-03-16
bump

---

