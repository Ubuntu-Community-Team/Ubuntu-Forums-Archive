---
title: "2 NICs, 1 wired and 1 wireless"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by adt41287 on 2009-07-04
What my objective is to connect wirelessly to the internet and with a separate wired NIC to stream media to my mythbox. 

Ok here is my setup:
(mythbox)<=wired=>(router)<=wired=>(server 9.04)<=wireless=>(internet)

and here is my dilemma everything for the most part works all fine and dandy, but not at the same time.  in order to use the internet on my server i need to take down my wired connection.

my ip configs go like so:
internet router - 192.168.1.1
server wlan0 - 192.168.1.20, 255.255.255.0, 192.168.1.1
server eth0 - 192.168.0.20, 255.255.255.0, 192.168.0.1
lan router - 192.168.0.1
mythbox eth0 - 192.168.0.22, 255.255.255.0, 192.168.0.1

I know this is a ICS issue but in everytime ive tried to setup ICS I could not get it working.  Ive been through [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") multiple times and ive tried the firestarter method.

By any means, networking is not my expertise.  I would love to understand more how this all works.  Also, on a side note Firestarter messed with my iptables, whats the easiest way to put them back to defaults??

thanks guys

---

### Post by cuschu on 2009-07-04
Just a thought, I'm not sure it will work this simply...but I think all you would need to do is edit the /etc/network/interfaces so that the gateway for all traffic to the 192.168.1.0 subnet is the address for the lan router and that the default gateway for all other traffic is the address for the internet router. So one line might look like this *up route add -net 192.168.1.0/24 gw 192.168.1.1 dev eth0* Here is a link that will be helpful if this is the solution.

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by superprash2003 on 2009-07-04
try using different subnet's for the server's wlan0 and eth0 . and how is the server getting the 192.168.0.20 ip?? you would want to make the server eth0 as gateway and your wifi router just as a hub

---

### Post by cuschu on 2009-07-04
If his wired connection is 192.168.0.20 and his wireless internet connection is 192.168.1.20 they are already on different subnets...at least both of those address are supposed to be Class C

---

### Post by adt41287 on 2009-07-05
> try using different subnet's for the server's wlan0 and eth0 . and how is the server getting the 192.168.0.20 ip?? you would want to make the server eth0 as gateway and your wifi router just as a hub

like cuschu just said they are on seperate subnets.  i got 192.168.0.20 through static routing, not dynamic.  I have my wifi (wlan0) setup statically too.  For eth0 should i make the gateway: 192.168.1.1 to the wifi router? and what about the gateways that are in the 192.168.0.X subnet? is it setup right as far as you can tell?

> Just a thought, I'm not sure it will work this simply...but I think all you would need to do is edit the /etc/network/interfaces so that the gateway for all traffic to the 192.168.1.0 subnet is the address for the lan router and that the default gateway for all other traffic is the address for the internet router. So one line might look like this up route add -net 192.168.1.0/24 gw 192.168.1.1 dev eth0 Here is a link that will be helpful if this is the solution.

[http://www.ubuntugeek.com/howto-add-...in-ubuntu.html](http://www.ubuntugeek.com/howto-add-...in-ubuntu.html)

thanks for the link ill look it over

---

### Post by alphacrucis2 on 2009-07-05
What you need to do first is to check your route table:


```
route -n
```

---

### Post by adt41287 on 2009-07-05
> **alphacrucis2 said:**
> What you need to do first is to check your route table:


```
route -n
```

here it is, whats up with all the 0's in the gateways??

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

---

