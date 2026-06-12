---
title: "Nautilus Samba Browse Interface"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by bonfire89 on 2010-08-21
Hi there,

I am only able browse my home samba network via nautilus if my wifi is on. I cannot if it is off.

I suppose this is because my computer is only set up to use wlan0 to browse.

How can I enable nautilus to browse samba shares via eth0.


Thanks!

---

### Post by Iowan on 2010-08-22
Kinda sounds like a routing problem...
Post results of **route -n** with wifi  and without it.

---

### Post by bonfire89 on 2010-08-31
sorry for my delayed response. I ran the commands as suggested and I thought since it has been a week I'd make sure the issue is still there and it turns out it is not. Which only adds the the confusion.

I suppose since I take my laptop on and off the network ever day something could have changed? I'm not sure.

I really appreciate the response though. I apologize for my issue being mysteriously resolved =/

But, I learned about a new command. 

Here is the output anyway


With Wifi on

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0

```

with wifi off

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 eth0

```

---

