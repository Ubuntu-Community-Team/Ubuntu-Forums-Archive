---
title: "DNS from other subnets"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by NoMojoMofo on 2009-05-14
Running Ubuntu 8.04LTS in a mostly windows domain.  Our intranet has multiple subnets.  The subnet the ubuntu machine is on has it's own domain, say,  xyz.com

The ubuntu machine has not been added to the windows security domain.

Currently I can access the ubuntu machine using <hostname>.local and just <hostname> but I need to use the IP if I VPN in from home or I'm on a machine on a different subnet.

DHCP provides IPs for all our hosts and other windows machines are addressable from other subnets by <hostname>.xyz.com but the ubuntu is not.

Are there settings I can change in ubuntu to let the DNS servers return the ubuntu IP for ubuntu-host.xyz.com?

---

