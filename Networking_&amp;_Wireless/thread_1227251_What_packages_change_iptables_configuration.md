---
title: "What packages change iptables configuration?"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by tlutz on 2009-07-30
I'm trying to configure iptables so I can bridge two networks and serve DHCP/DNS with NAT on a third.  I have a configuration for my iptables that works properly, but I notice upon reboot that the policies of INPUT, FORWARD, and OUTPUT change to DROP, and my rules are replaced by other rules.  What packages that are part of a typical Ubuntu Desktop installation would affect my iptables configuration?

These are the only ones I can think of:
network-manager
network-manager-gnome
firestarter

I imagine any other packages that touch iptables would be in the subset of packages that are included in the Desktop installation and not in the Server installation.

Thanks in advance!
Tom

---

