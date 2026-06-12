---
title: "Questions about the /etc/network/interfaces file &quot;gateway&quot; command on Ubuntu"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2012-01-24
Two questions:
1. Is there a way to set the gateway without rebooting?
2. Does it matter if the gateway is still set up after rebooting?

I just set up an antenna and radio connection to a WISP access point, and in doing so, I learned some networking hints that may help others.

For example, if you want to connect to the Internet without a router in between your radio and your laptop, you'll need to set the gateway on the laptop:

[LIST]
[*]This is the (test) connection WITHOUT the router:
[LIST]
[*]Laptop eth0 -> POE -> Radio -> Antenna
[/LIST]
 
[*]This is the (permanent) connection WITH the router:
[LIST]
[*]Laptop eth0 or wlan0 -> Router LAN -> Router WAN -> POE -> Radio -> Antenna
[/LIST]
 
[/LIST]
To set the gateway, I changed the /etc/network/interfaces
FROM:
```
auto lo
iface lo inet loopback

```TO:
```
auto lo
iface lo inet loopback
gateway 10.0.23.1
```Only after making that change and rebooting the laptop, was I able to connect from the laptop directly to the radio at the rooftop antenna, and then to the Internet.
$ sudo ifconfig eth0 10.0.23.10 netmask 255.255.255.0
$ telnet 10.0.23.2 80

My questions:
1: Could I have set the gateway on Ubuntu without rebooting?
2: Must I remove that gateway command once I add a home broadband router?

---

