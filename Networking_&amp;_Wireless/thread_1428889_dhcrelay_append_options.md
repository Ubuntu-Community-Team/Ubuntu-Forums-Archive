---
title: "dhcrelay append options?"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by jeff.sadowski on 2010-03-13
Ok here is the situation.

I want it so when I take my laptop to a network that does not have dhcp servers with "next-server" and "filename" options that my laptop will be able to take pxe boot requests and point it to itself.

Can dhcrelay add these options?

Or do I need to setup dhcpd3 with options to only respond on the port for bootp? (setup a second ipaddress on eth0:0 to handle bootp requests)

I do not want my laptop acting as a router or to be depended upon for the pxe boot images I load from it. When the images boot far enough they will request a dhcp address.

---

