---
title: "Printing on different subnet"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by biodojo on 2012-08-15
Hello,

Our network admin recently created VLAN's with different IP address subnets (one for wired 10.3.64.x and one for wireless 10.3.145.x with a subnet mask of 255.255.240.0). Currently there are not access restrictions accross the VLANs. I can ping from one subnet to another via IP address and hostname, but I cannot print across the subnets (from a wireless Ubuntu laptop running 12.04 to a wired printer). I can add the printer and can print if I plug the laptop into a wire, but on wireless I get this error in the printer state:

Idle - /usr/lib/cups/backend/hp failed

Windows laptops can print across the subnets. The printers are shared on a Windows 2008 server. I am thinking of asking the network admin to change the subnet mask to 255.255.0.0 to allow wireless devices to see the same subnet as wired, but he probably won't for security purposes, so I am looking for other ideas.

---

