---
title: "Ubuntu Multihoming Non-router Server &quot;Default Gateway&quot;/Egress Interface Issue"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by trbooth on 2009-10-08
Hello,

I am running Ubuntu server with two NICs. I'm having no issues with functionality of the NICs or setup thereof.

Here's the route table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.5.0       *               255.255.255.240 U     0      0        0 eth0
10.10.0.64      *               255.255.255.240 U     0      0        0 eth1
default         10.10.0.65      0.0.0.0         UG    100    0        0 eth1
default         10.10.5.1       0.0.0.0         UG    100    0        0 eth0
```Depending upon which default route sets up *last*, one particular interface seems to be set up as a designated default interface (despite identical metrics). Traffic leaving the server destined for a non-"connected" route (a route outside both directly-connected subnets e.g. 10.10.1.0/24) goes through **only that one** interface regardless of which interface is the ingress (and source) interface.

How can one set it up so that **no** traffic  sourced from one interface leaves via the other (the same going for both interfaces)?

---

### Post by spd106 on 2009-10-09
Sounds like you need to set-up policy based routing.

Useful links:
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)
[http://www.debian-administration.org/article/Policy_routing](http://www.debian-administration.org/article/Policy_routing)

---

### Post by trbooth on 2009-10-12
That's strange. To require policy routing to simply have packets leave from the originating interface (when all else is equal) seems a bit dysfunctional.

---

