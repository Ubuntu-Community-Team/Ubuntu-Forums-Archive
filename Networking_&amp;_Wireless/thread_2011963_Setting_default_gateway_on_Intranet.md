---
title: "Setting default gateway on Intranet"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by M4DM4DZ on 2012-06-28
Hey guys, I've got a Single server running Lubuntu 12.04 with one network interface (eth0, 10.10.1.1).

This is connected to a Netgear Wireless access point with DHCP Disabled. The Lubuntu box is hosting DHCP and running a web server on port 80/443

Because there is no security on the WAP, I want public users to connect to the Wifi, open their web browser and have it instantly go to my intranet website regardless what the browsers home page is set to.

Remember, this is a local LAN network, there is no gateway to the internet here, just one machine physically plugged into the LAN port on the Access point. (not the gateway port)

Whats the best way to make this happen? do i need to use iptables, or run a DNS server?

The DCHP server is running fine, public members can access the webserver but currently have to type the address into the browser [http://10.10.1.1](http://10.10.1.1)

Im sure theres a simple answer to this, hope some one can help

Cheers

---

