---
title: "IPv6 routing issue"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by rivy on 2013-02-18
Hi all,

I'm having a IPv6 routing problem. I have 2 directly connected machines. 

MachineA has a route for a certain network. That route is pointing towards machineB. 

When I try to ping6 hosts within that certain network, all I get is "network is down" although I can ping MachineB.

I have a similar setup for IPv4 and that works without issues. I'm pretty sure, the exact same setup worked fine with Ubuntu 10.04. Unfortunatelly, I can't easily test that anymore.

More details are available on this blog post.
[http://www.rivy.org/ipv6-ping-sendmsg-network-is-down/](http://www.rivy.org/ipv6-ping-sendmsg-network-is-down/)

Did anyone experience the same issues or know how to solve them?

Best regards,
Thomas

---

### Post by lemming465 on 2013-02-20
What do the v6 routes on machine B look like?  And does machine B have IPv6 forwarding on, and ip6tables rules allowing the traffic?

---

### Post by rivy on 2013-03-03
This was fixed after rebooting host A. I have no idea what the real problem was.

Best regards,
Thomas

---

