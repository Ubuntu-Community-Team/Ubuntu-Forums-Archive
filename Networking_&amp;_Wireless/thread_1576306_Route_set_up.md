---
title: "Route set up"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by liuhb86 on 2010-09-17
There are two connections in my Ubuntu server:

eth0 is a normal interface and,
eth1 is configured with an static IP, and has an domain name with that IP. But this connection is charged by bytes, very expensive.

My question is how to set up the route table so that:

everyone can access my server with the domain name, and
let the traffic goes from eth0 as much as possible(I have a proxy service on my server.
At least, let the proxy traffic goes from eth0)?

My current route is:
x.x.81.0    *               255.255.255.0   U     0      0        0 eth1
x.x.81.0    *               255.255.255.0   U     0      0        0 eth0
default         x.x.81.1    0.0.0.0         UG    100    0        0 eth0
default         x.x.81.1    0.0.0.0         UG    100    0        0 eth1

, which made the server inaccessible from outside by hostname.

---

### Post by Iowan on 2010-09-17
Two gateways is usually a problem. The gateway is for "everything else" - so it ordinarily points to the internet-facing interface.

[Here]("http://ubuntuforums.org/showthread.php?t=1574499") is a similar thread  where two connections were via two different ISP's...

---

