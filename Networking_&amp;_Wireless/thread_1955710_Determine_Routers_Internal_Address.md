---
title: "Determine Routers Internal Address"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by borgward on 2012-04-10
How do I determine my routers internal address using the command line? I know it could be 192.168.bla.bla. Assume it is brand X, and the user manual does not state what the internal address is. It is dfinitely not 192.168.1.1, 192.168.0.1, 192.168.2.1, etc.

The router is known good, ethernet cable is known good.

I want to be able to determine the routers internal address using the command line.

I tried ifconfig and the with options -a, -n, -s, -v.

---

### Post by Doug S on 2012-04-10
I would look at the route:```
doug@s15:~$ [COLOR=red]route[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         [COLOR=red]192.168.111.1[/COLOR]   0.0.0.0         UG    100    0        0 eth0
192.168.111.0   *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0

```My router is at 192.168.111.1

---

### Post by borgward on 2012-04-10
All route displays is:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

Nothing else.

---

### Post by borgward on 2012-04-10
My Bad

Route does display the info. The router/powersuppl, plug/receptical is loose, allowing the power to cycle on and off w/o me knowing it.

---

