---
title: "DHCPD:  Different IPs for different VLANs"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by amckenzie on 2010-01-26
So I've been working on this for a while, and I'm hoping someone here can point me in the right direction.

The background:
I have a server which is on two VLANs, using a single physical interface.  Actually, it will be a little more complicated, but for testing purposes I've pared it down to this.  The interfaces are defined as eth0.1211 and eth0.1212.  For testing, the subnets are 10.12.1.0/24 and 10.12.2.0/24 -- we'll be redefining things when we go to production.

The problem:
I need to have clients which can move from one VLAN to the other, and get a different IP address in each.  Given that host declarations in DHCPd are global, and I can't find a way in dhcpd.conf to bind a client address to an interface, how do I make that happen?  I'll also want to have a small pool for unknown clients on each subnet, which will, of course, need to be only used for clients on a given VLAN.

If anyone can give me at least a starting place, I'd appreciate it!

Thanks,
  Alex

---

