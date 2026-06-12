---
title: "shorewall and static and routing in xen"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by pbrille on 2010-01-05
Hi,

I use a EQ 4 dedicated root server by hetzner. I installed xen and brought up 3 domUs.
Now comes networking...
Hetzner does not allow bridged networking so I have to use routed mode in xen. No Problem so far, but the Problem I see is:
When I bring up a domU the routing table is created by the xen-script vif-routing. The network interface name for this is created dynamically, depending on the domU ID.

Example:
If the domU ID is 16, the network interfaces name will be vif16.0 in the dom0. So I tell shorewall that it shall ACCEPT traffic from an to vif16.0. The next time I restart my server or just the domU, there's a new network interface name, that the shorewall firewall does not know...

As far as I know there's no way to tell a xen domU to get a static ID, so the network interface name would be static as well.
Any Ideas or solutions?

Edit:
figured it out myself:
vifname=xeneth1

---

