---
title: "Access remote host via multiple subnets?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by mjscott2702 on 2009-06-08
Hello,
I am running Ubuntu 8.04 on a system with 2 NIC cards, connected to different subnets (eth0 -> 10.1.1.x and eth1 -> 10.1.2.x). The reason is to allow communication for data-intensive operations on a dedciated subnet, without flooding the main "network".

I can connect to machines (via ip-addresses) on either subnet e.g 10.1.1.8 or 10.1.2.8 both connect to the same machine.

I'd like to have some kind of preferential "fail-over" - connect to other 10.1.2.x machines via eth1, or if not available, connect via the 10.1.1.x subnet.

Ideally, this would just be done via "aliasing" - I tried putting two different IP addresses with the same canonical name, but the Ubuntu machine always uses the first, and if I disable the 2nd NIC, can no longer ping it.

Is there an easy way of doing this? Am I approaching it all wrong? There is no gateway between the subnets, as I want to keep them isolated from each other.

---

### Post by DGortze380 on 2009-06-08
> **mjscott2702 said:**
> 
I'd like to have some kind of preferential "fail-over" - connect to other 10.1.2.x machines via eth1, or if not available, connect via the 10.1.1.x subnet.

Is this going to be physically possible?

A network map (general) would help.

To the best of my knowledge, you would do this with iptables. Going to search now because I'm curious.

---

### Post by DGortze380 on 2009-06-08
> **mjscott2702 said:**
> Hello,
I am running Ubuntu 8.04 on a system with 2 NIC cards, connected to different subnets (eth0 -> 10.1.1.x and eth1 -> 10.1.2.x). The reason is to allow communication for data-intensive operations on a dedciated subnet, without flooding the main "network".

I can connect to machines (via ip-addresses) on either subnet e.g 10.1.1.8 or 10.1.2.8 both connect to the same machine.

I'd like to have some kind of preferential "fail-over" - connect to other 10.1.2.x machines via eth1, or if not available, connect via the 10.1.1.x subnet.



Ok. Like I said, I network map would be very helpful.
But after some thinking (how I see your set up in my head), I think you simply need a few static routes.

If you add a default route on the ubuntu machine similar to:

dest 10.1.2.0 gateway 10.1.1.0 (address of the router/gateway on your .1 subnet) int eth0

Then add your main, normal routes above it.

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

I'm just not sure of the fall through. I believe if an interface goes down it should fall through to the default route. Someone please correct me if I'm wrong.

---

