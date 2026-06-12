---
title: "WUG - How do I set up my network for both the Interent and WUG  at the same time?"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Funkey Monkey on 2010-08-27
Hello ):P,

There is 2 networks that I would like to be part of
a) Through my wlan0 --> Internet DSL
and
b) Through my eth0 --> WUG - PTAWUG 

I can only get one of the networks to work at 'n time.

The wlan0 works fine when I start my PC, but when I want to access the WUG I need to do the following command:
```

sudo route add -net 172.16.0.0 netmask 255.240.0.0 gw 172.24.6.177 dev eth0
```

with the above command, I can then access the WUG but not the internet through my wlan anymore.

My **_[SIZE="4"]Ideal solution[/SIZE]_** would be that all data goes to my wlan as standard unless its on the 172.16.0.0 network

Please guide me to reach my solution

---

### Post by Iowan on 2010-08-27
What does the routing table look like (**route -n**) before/after you add the route?

---

### Post by Funkey Monkey on 2010-08-27
**_LAN cable UNplugged:_**
```
x@x-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
```

**_With LAN cable plugged in:_**
```
x@x-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.24.6.176    0.0.0.0         255.255.255.248 U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
```

**_Then after I ran the command:_**
```
x@x-laptop:~$ sudo route add -net 172.16.0.0 netmask 255.240.0.0 gw 172.24.6.177 dev eth0
[sudo] password for x: 
x@x-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.24.4.166    0.0.0.0         255.255.255.255 UH    0      0        0 eth0
172.24.6.176    0.0.0.0         255.255.255.248 U     1      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.16.0.0      172.24.6.177    255.240.0.0     UG    0      0        0 eth0
0.0.0.0         172.24.4.166    0.0.0.0         UG    0      0        0 eth0

```

[COLOR="Blue"][SIZE="3"]Thank You for taking an interest in my problem. I hope you can help me.[/SIZE][/COLOR]:D

---

### Post by Funkey Monkey on 2010-09-12
BUMP with Hope.

How can I make wlan my standard "route", and make data flow to eth0 if it is adressed to 172.x.x.x ???

---

### Post by Iowan on 2010-09-12
Aside from the netmask, it looks like the original cabled version is what you want.

---

### Post by MaindotC on 2010-09-12
[Here's a thread](http://ubuntuforums.org/showthread.php?t=234207) for adding a permanent entry so you shouldn't have to keep on entering it when you connect.

---

