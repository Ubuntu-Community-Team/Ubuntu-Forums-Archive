---
title: "How do I enable a VLAN trunk with one physical interface?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by b0ot on 2010-07-26
I would like to be able to route between vlans from a switch with Ubuntu 10.04

Currently I have:
- Installed the Vlan package
- set net.ipv4.ip_forward = 1 (located in /etc/sysctl.conf)
- modprobe 8021q

I also tried to do
  sudo vconfig add eth0 10
  sudo vconfig add eth0 20
  sudo vconfig add eth0 30

to add vlans 10,20,30 to eth0.

If anyone could provide an explanation of what needs to be done, and why I would appreciate it greatly. The documentation for this subject (that I have been able to find) has been very old, and didn't really say what/why certain steps were taken.:(



Thanks,

---

