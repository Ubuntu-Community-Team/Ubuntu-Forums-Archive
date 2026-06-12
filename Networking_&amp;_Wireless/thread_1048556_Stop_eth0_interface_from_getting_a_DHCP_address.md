---
title: "Stop eth0 interface from getting a DHCP address"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by wiseguyxp on 2009-01-23
I have my eth0 interface bridged with tap0 so I can have a bridged vpn.  The bridge interface (br0) gets a dhcp address from the network, which is fine, but the eth0 keeps getting one, which then kills my connection because it is no longer in promisc mode.  Is there a way that I can keep eth0 from getting an IP address and blowing up my bridge?

---

### Post by Kebabman on 2009-01-23
you should be able to edit the file '/etc/network/interfaces' and remove the line 'iface eth0 inet dhcp'

---

### Post by wiseguyxp on 2009-01-24
The only interface in my interfaces file is lo.  It doesn't say anything about eth0.

---

