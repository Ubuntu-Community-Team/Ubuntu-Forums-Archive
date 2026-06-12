---
title: "find gateway + DHCP server +DNS server from CLI"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by boondocks on 2010-05-27
On a remote system, when all you have is the ssh CLI - how do you find out the ip addresses for:
[LIST]
[*]the Gateway
[*]the DHCP server
[*]the DNS server
[/LIST]

Don't need to make any changes.
Which commands will display this info?

---

### Post by chili555 on 2010-05-27
Gateway:```
route -n
```For example:> $ route -n
Kernel IP routing table
Destination     [COLOR="Red"]Gateway[/COLOR]         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         [COLOR="Red"]192.168.1.254 [/COLOR]  0.0.0.0         UG    100    0        0 wlan0Usually, the gateway and the DHCP server are the same.

DNS server:```
cat /etc/resolv.conf
```For example:> $ cat /etc/resolv.conf
nameserver 192.168.1.254
domain gateway.2wire.net
search gateway.2wire.netIn this case, the router contains the actual DNS nameservers. To get the actual DNS nameserver addresses, you'd likely have to log on to the router's administration pages.

---

