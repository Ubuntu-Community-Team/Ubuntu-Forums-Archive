---
title: "binding a virtual interface"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by kufkis on 2011-11-18
I have a virtual interface that is importing live traffic from a wireless router on the network but it has no encapsulation.  I want to change it to Ethernet but anytime i run "ifconfig kistap0 hw ether 1A-87-AE-7D-EC-44" I get an error of invalid Ether address.  I've tried putting an IP address in place of the mac, configuring while the interface is down, using other macs and IPs, but nothing seems to change the encapsulation.  I am also working in an ssh session only.

This system also has a couple of spare ethernet cards that are not in use, so I'm open to binding this virtual interface to a NIC so it will use the NICs already configured settings, if that's any easier or possible.



to recap:
I have a wireless router forwarding its traffic (layer 2 & 3) to this server, via an unencapsulated raw virtual interface, and I need to change the encapsulation of it or bind it to a spare NIC so other programs can see the layer 3 traffic on it.  Assigning it an IP does not seem to help either.

Thanks

---

