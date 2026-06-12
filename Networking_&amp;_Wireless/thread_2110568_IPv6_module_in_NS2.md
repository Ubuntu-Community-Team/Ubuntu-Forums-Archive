---
title: "IPv6 module in NS2"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by JawadHussain on 2013-01-30
Dear everyone,
I am a bit new with Linux and NS2. So please guide me if i'm wrong in asking the question.
I want to check the effect of IPv6 on latency and throughput of a  network. I got results (available on internet) of latency and throughput  of different protocols with IPv4 but now i want the results using  IPv6.....
I am planning to use NS2 but unfortunately I am unable to find any support in NS2 regarding IPv6. Please help me....
Thanking you in advance.

---

### Post by lemming465 on 2013-01-31
I'm unclear on whether you want measured results or simulated results.  If simulated, you might prefer [NS3]("http://www.nsnam.org/") to NS2; I haven't used either, but a quick glance at the documentation suggests the IPv6 support is better in NS3.

Measured IPv6 results depend heavily on the path and equipment, due to native versus tunneled, hardware assist versus software-only implementations, etc.  In general, on enterprise gear, IPv4 and IPv6 performance should be similar.  In a test lab with Cisco gear on gigabit ethernet I lose about 4% on TCP net data throughput to the bigger IPv6 packet headers; my packet forwarding rates and ethernet bit rates are basically identical.

Teredo tunneling will be very bad (very high latency, failure rates of 35%); 6to4 tunneling will also be bad.  6in4 tunnels with a broker will add significant latency (30ms?) but have decent success rates.  Whereas 6rd inside an ISP will probably only add 3ms or so to latency.

RIPE, Geof Huston at APNIC, and Hurricane Electric etc. have some statistics on live IPv6 deployment reach and latency:
> [http://ttm.ripe.net/ttm/Plots/IPv6/](http://ttm.ripe.net/ttm/Plots/IPv6/)
[http://www.potaroo.net](http://www.potaroo.net)
[http://ipv6.he.net](http://ipv6.he.net)

---

### Post by JawadHussain on 2013-04-08
dear lemming465, its very nice of u that u answered my question.
I  actually wanted to simulate IPv6 network in ns-2, for that i am looking  for IPv6 modules or is there any way that i may create an IPv6 scenario in ns-2????

---

