---
title: "Ubuntu server 12.04 issue on forwarding from a wireless subnetwork"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by Florin C on 2013-02-08
Hi,

I have an issue with a Ubuntu server box running 12.04.

This box is a gateway for my network (eth0 is inet, eth1 is local network). In the LAN I have one PC and a Linksys wireless router that can have multiple wireless devices (laptop, kindle, tablet, etc).
The problem appeared AFTER I upgraded from Ubuntu 11 to 12. Before that everything worked fine, accessing the internet from those wireless devices worked.
After upgrade I was in the following situation: The tablet & kindle could not FULLY access the net (for ex. could access some news sites, but not google.com) but the laptop worked normally. The PC from local lan worked correctly.
If I put the wireless router as gateway for inet all devices are working fine.
I also, on UBox, fully enabled the iptables firewall (without any restrictions) and the issue still in place.

So, right now I can't fully use my kindle (store access and browse for some sites) and my tablet. For example, for google.com accessed from my tablet I've get a lot of time exceeded ICMP. Rising TTL is not helping, so probably those TE are because of some packet loose over the network or ?in_the_gateway?
I don't want to downgrade to Ubuntu 11 or to switch to another Linux distribution. At least for now.

Any idea why this is happening? Is something wrong with the kernel 3.x.x regarding the forwarding functionality?

Thanks!

---

