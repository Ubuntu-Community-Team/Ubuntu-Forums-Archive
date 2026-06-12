---
title: "Broadcom on Dell 1100 works but only with 1 access point"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by marknewlyn on 2006-07-10
Hi 

I have an inspiron 1100 with a Truemobile 1300 (Broadcom) card. Wireless has been working for me using the driver provided in the forums for the kernel module but only when there is only 1 access point identifying itself with the same essid.

On travel (at hotel, conference etc.) there are usually multiple access points all with the same essid. What I get are multiple entries with the same name in the drop down menu in the configure part of the network manager. I can select one but I never can connect.

If I try a iwlist scan I see many entries with the same essid but I  just cant' connect. 

I don't know where to start to solve this. Please could someone point me in the right direction?

Thanks

Mark

---

### Post by marknewlyn on 2006-07-10
Here is what happens when I start the network:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:56:eb:56:66
Sending on   LPF/eth0/00:0d:56:eb:56:66
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 18.71.0.31 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:10:c6:2d:87:2c
Sending on   LPF/eth1/00:10:c6:2d:87:2c
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 18.7.21.127 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:56:eb:56:66
Sending on   LPF/eth0/00:0d:56:eb:56:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:10:c6:2d:87:2c
Sending on   LPF/eth1/00:10:c6:2d:87:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 18.188.64.4
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPOFFER from 18.188.64.4
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 18.188.64.4
SIOCADDRT: File exists
bound to 10.188.74.95 -- renewal in 51 seconds.
                                                                         [ ok ]

---

