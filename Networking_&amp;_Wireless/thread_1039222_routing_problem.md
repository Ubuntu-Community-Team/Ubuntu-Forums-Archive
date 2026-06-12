---
title: "routing problem"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by Underpants on 2009-01-14
I have two linux boxes acting as routers between two buildings. 


Traffic is 100 percent between machines on both subnets (not including the linux boxes)
192.168.7.7 can talk to 192.168.1.40 and vise versa. 

I am working on lnxcorp. 
"ping 192.168.7.7" results in 100 percent packet loss.
"ping -I 192.168.1.220 192.168.7.7" works great. 

So basically each linux box cannot see the "other" sides subnet. But the problem only exists on the linux boxes. The clients on both subnets see each other just fine



```
Network topology

192.168.1.0/24 - corp network

192.168.1.220 - eth0 lnxcorp
192.168.2.100 - eth1 lnxcorp

192.168.2.101 - eth1 lnxiii
192.168.7.220 - eth0 lnxiii

192.168.7.0/24 - iii network


addresses of a server on each network

192.168.1.40 - machine on corp network
192.168.7.7 - machine on iii network



Routes added to linux boxes

lnxcorp:
# connects eth1's between buildings
!!!route add -net 192.168.2.0 netmask 255.255.255.0 dev eth1
# lets local machine know about remote subnet
route add -net 192.168.7.0 netmask 255.255.255.0 gw 192.168.2.101


lnxiii:
# connects eth1's between buildings
!!!route add -net 192.168.2.0 netmask 255.255.255.0 dev eth1
# lets local machine know about remote subnet
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.2.100


Routing tables

gwik@lnxcorp:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     192.168.2.101   255.255.255.0   UG    0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.4     0.0.0.0         UG    100    0        0 eth0


gwik@lnxiii:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.7.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.1.0     192.168.2.100   255.255.255.0   UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.7.1     0.0.0.0         UG    100    0        0 eth0

```

---

