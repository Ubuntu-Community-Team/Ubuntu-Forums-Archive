---
title: "Set up two ip's"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by DarknessMonk on 2010-07-12
How can i set up two ip's on the same NIC? I need one high ip (for testing web applications) and a low ip (to connect to the intranet servers).

Thanks in advance,
Leo

---

### Post by Brandon Williams on 2010-07-12
How are you configuring your interfaces? If you use /etc/network/interfaces (as opposed to network-manager), you'll find config examples in /usr/share/doc/ifupdown/examples/network-interfaces.gz, such as:
```
# auto eth0 eth0:1
# iface eth0 inet static
#     address 192.168.0.100
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
# iface eth0:1 inet static
#     address 192.168.0.200
#     network 192.168.0.0
#     netmask 255.255.255.0
```
In this case, both addresses are static, but that doesn't have to be true of either one. I've used this method to add multiple dhcp assigned addresses to a single machine, too. The only important part is appending the ":<number>" to the interface name in the second case.

---

### Post by DarknessMonk on 2010-07-12
Thanks Brandom...
Well, i was using the /interfaces file (and the /etc/resolv.conf to specify a nameserver). Still, even using the below config, i can't seem to ping on a low ip machine... But if i make eth0:1 -> eth0 and eth0->eth0:1, i do ping. There exists any kind of hierarchy on these adaptors?

Thanks in advance,
Leo.

```
auto lo eth0 eth0:1

iface lo inet loopback

iface eth0 inet static
address 200.17.141.175
netmask 255.255.255.0
gateway 200.17.141.129
broadcast 200.17.141.255

iface eth0:1 inet static
address 192.168.77.153
netmask 255.255.192.0
gateway 192.168.64.3
```

> **Brandon Williams said:**
> How are you configuring your interfaces? If you use /etc/network/interfaces (as opposed to network-manager), you'll find config examples in /usr/share/doc/ifupdown/examples/network-interfaces.gz, such as:
```
# auto eth0 eth0:1
# iface eth0 inet static
#     address 192.168.0.100
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
# iface eth0:1 inet static
#     address 192.168.0.200
#     network 192.168.0.0
#     netmask 255.255.255.0
```In this case, both addresses are static, but that doesn't have to be true of either one. I've used this method to add multiple dhcp assigned addresses to a single machine, too. The only important part is appending the ":<number>" to the interface name in the second case.

---

### Post by Brandon Williams on 2010-07-12
You generally don't want to specify two different gateway's unless you also specify metrics to declare the order of preference for the two gateways. So each one is accessible via the same physical network, the most likely case is that your eth0:1 should just have the gateway setting removed. That's probably not the source of your trouble, though, unless you're trying to ping an address that is not on the local network and one of the two gateways is not properly configured.

Do you know where the packets are getting hung up? Have you tried running traceroute to figure out how far your packets are getting?

---

### Post by DarknessMonk on 2010-07-12
Well, i need two different gateways because with the high ip, i have direct internet connection and with the low ip i'm behind a proxy and some resources are blocked to all but to the proxy ip. I'll try to traceroute tommorow and post the log here. Thanks for the quick answer!

---

### Post by Brandon Williams on 2010-07-13
Proxy requirements are not something to resolve with generic routing table settings. To make it work correctly, you'll have to do something more complicated than just defining two different default gateways. There's nothing in your configuration to guarantee that you will use the correct gateway. What you want is policy based routing, since it will allow you to tell the system to use the low IP gateway as the default when sending from the low IP address, and to use the high IP gateway when sending from the high IP address.

For example, with just the high IP default gateway specified in your /etc/network/interfaces file, I would expect to see an ip configuration something like the following:
```
$ sudo -i
# ip addr show eth0 | grep inet
inet 200.17.141.175/24 brd 200.17.141.255 scope global eth0
inet 192.168.77.153/18 brd 192.168.127.255 scope global eth0:1
# ip route show
200.17.141.0/24 dev eth0  proto kernel  scope link  src 200.17.141.175
192.168.64.0/18 dev eth0  proto kernel  scope link  src 192.168.77.153 
default via 200.17.141.129 dev eth0  metric 100
# ip rule show
0:	from all lookup local 
32766:	from all lookup main 
32767:	from all lookup default
```
Then, to add the necessary policy based routing on the command line, you would do something like this:
```
# echo "1 proxygw" >> /etc/iproute2/rt_tables
# ip route add 192.168.64.0/18 dev eth0 src 192.168.77.153 table proxygw
# ip route add default via 192.168.64.3 dev eth0 table proxygw
# ip rule add from 192.168.77.153/32 table proxygw
```
What the above does is to create a new routing table called proxygw, add a default gateway setting to that table, and then create a rule that will send all packets from 192.168.77.153 to the proxygw table for routing.

Look at 'man 8 ip' to get more information about the ip command and how to do policy based routing.

---

