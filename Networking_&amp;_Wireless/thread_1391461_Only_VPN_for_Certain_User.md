---
title: "Only VPN for Certain User?"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Azureon2 on 2010-01-26
Is it possible to configure Ubuntu such that a certain non-privileged user can only access the net through a VPN?  I have an ethernet connection eth0 and a VPN network connection ppp0, and I'd like for the non-privileged user to run through ppp0 and not eth0.  It's easy enough to block the user from using eth0, telling iptables:

iptables -A OUTPUT -o eth0 -m owner --uid-owner [nonprivileged-username] -j REJECT

However, while that blocks the user from sending outbound traffic from eth0, I can't configure the user to use ppp0 instead.  This user can't modify the routing table, since it is a nonprivileged user, and I'd prefer not to have to make global modifications to the routing table anyway since other users on the system still need to use eth0.

Thanks!

---

