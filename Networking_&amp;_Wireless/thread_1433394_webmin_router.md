---
title: "webmin router"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by reggler on 2010-03-19
Hi there,

I'm trying to get a router configured using webmin this is how far i've gotten if **eth1** is the iface connected to the modem and **eth0** the internal LAN interface:
[LIST]
[*]I set **net.ipv4.ip_forward=1** in **/etc/sysctl.conf**
[*]I did a **echo 1 > /proc/sys/net/ipv4/ip_forward**
[*]I configured following rules in webmin:
**Incoming packets (INPUT)**
Accept	If input interface is lo		
Accept	If input interface is eth1 and state of connection is ESTABLISHED,RELATED		
Accept	If input interface is eth0
**Forwarded packets (FORWARD)**
Accept	If input interface is eth1 and output interface is eth0 and state of connection is ESTABLISHED,RELATED		
Accept	If input interface is eth0 and output interface is eth1
[/LIST]
Now i got eth1 configured to be a dhcp client (from the modem) and eth0 is configured to 192.168.101.1 which is fine ping-able but from my network i seem not to be able to see the internet, why not? What am I missing/forgetting?

Thank you!
roN

---

### Post by koszta on 2010-03-19
first I would try to turn off this firewall completely and see if that is the thing that causes the problem. 
Second make sure that eth1 has a correct IP address
Third ensure that the default route for eth0 is eth1 (or just add a route if you want to use different one as a default. You can do this by route 
```
route add -net 192.168.101.0 netmask 255.255.255.0 (I am guesing) dev eth1
```
Forth ensure that all the pcs in LAN have eth0 as their default route. 

Fifth -> try the "traceroute" command (tracert on Win) e.g. traceroute IP_of_eth1 from a machine within the LAN. It will show you where the packets get stuck and should also give you ICMP msg and therefore an idea what wrong

---

### Post by reggler on 2010-03-20
> **koszta said:**
> first I would try to turn off this firewall completely and see if that is the thing that causes the problem. 
Second make sure that eth1 has a correct IP address
Third ensure that the default route for eth0 is eth1 (or just add a route if you want to use different one as a default. You can do this by route 
```
route add -net 192.168.101.0 netmask 255.255.255.0 (I am guesing) dev eth1
```
Forth ensure that all the pcs in LAN have eth0 as their default route. 

Fifth -> try the "traceroute" command (tracert on Win) e.g. traceroute IP_of_eth1 from a machine within the LAN. It will show you where the packets get stuck and should also give you ICMP msg and therefore an idea what wrong

Shouldn't the route be setup like:
```
route add -net 192.168.101.0 netmask 255.255.255.0 (I am guesing) dev eth**0**
```???
My current routes look like this:
```
192.168.101.0   *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

```

if i traceroute 102.168.1.101 (eth1 ip) i just get the following:
```
traceroute to 192.168.1.101 (192.168.1.101), 30 hops max 60 byte packets
1  192.168.0.1 (192.168.0.1) 1.313ms 1.615ms 1.888ms
2  * * *
...
30 * * *
```
This doesn't tell us much, does it? :(

---

