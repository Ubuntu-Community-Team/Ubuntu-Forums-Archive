---
title: "Ghost MAC address on Ubuntu server causing problems to DHCP server"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by globemast on 2012-04-11
Hi all,

The last few days, our DHCP server reports that every few minutes a machine in our network (with a specific MAC address) is requesting an IP with wrong subnet details. Our network switch indicates that a node with the given MAC address is connected on one specific port.

On this port, there is one IBM server running Ubuntu 11.04 Server 64-bit, however this machine has no network interface with such a MAC address (checked with ifconfig -a). We changed ports on the switch to check if this was a port hardware problem however it is not. The MAC address continues "spamming" the DHCP server from the new port.

The Ubuntu Server distribution on this machine has no VM support such as VMware, Xen etc. 

I would highly appreciate any help for tracking what is causing this problem, and where this ghost MAC address could be coming from the machine.

Regards.

---

### Post by globemast on 2012-04-12
Hi, any suggestions on the above???

---

