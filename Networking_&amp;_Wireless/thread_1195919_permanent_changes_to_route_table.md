---
title: "permanent changes to route table"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by jmk123 on 2009-06-24
here is my issue, at start up the route table is thus:
% route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.5     0.0.0.0         UG    100    0        0 eth0

the default metric is 100, but i need a metric of 0!
so i do this:
% route del default
% sudo route add default gw 192.168.2.5 metric 0 eth0

now i get:
% route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.5     0.0.0.0         UG    0      0        0 eth0


now everything works great!  however, every time i restart networking, it gets reset and i have to do this all over again.  any suggestions on making this change permanent?  thanks!

---

### Post by jonobr on 2009-06-24
Hello


The common way of adding a route after startup is to go to
/etc/network/if-up.d and create a file called static-route and make sure its permissions make it executable.

From there put in

```

#!/bin/sh
# Insert static routes
#


/sbin/route del -net default gw x.x.x.x netmask y.y.y.y dev eth0
/sbin/route add -net x.x.x.x gw x.x.x.x netmask y.y.y.y dev eth0
```


I would test this as I have only really done this with adding new routes, not modifying the default one

Cheers

---

