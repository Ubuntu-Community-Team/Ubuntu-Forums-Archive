---
title: "dhcpd3-server will not start"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by achaycock on 2009-04-13
Hi folks, I'm running Ubuntu Server 8.10 and have hit a problem with the DHCP server consistently failing to start. This appears to have manifested after installing FOG, although I have manually configured my dhcpd.conf file to this;

[HTML]ddns-update-style none; 

option domain-name "haycock.local";

option domain-name-servers 192.168.0.3, 192.168.0.5; 

default-lease-time 86400; 

max-lease-time 604800; 

authoritative; 

subnet 192.168.0.0 netmask 255.255.255.0 { 

range 192.168.0.100 192.168.0.150; 

option subnet-mask 255.255.255.0;

option broadcast-address 192.168.0.255;

option routers 192.168.0.1; 

} 
[/HTML]

Looking at the syslog, it gives me this information

[HTML]Apr 13 10:32:14 SVR-S02 dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Apr 13 10:32:14 SVR-S02 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Apr 13 10:32:14 SVR-S02 dhcpd: All rights reserved.
Apr 13 10:32:14 SVR-S02 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr 13 10:32:14 SVR-S02 dhcpd: Wrote 0 leases to leases file.
Apr 13 10:32:14 SVR-S02 dhcpd: socket: Address family not supported by protocol - make sure
Apr 13 10:32:14 SVR-S02 dhcpd: CONFIG_PACKET (Packet socket) and CONFIG_FILTER
Apr 13 10:32:14 SVR-S02 dhcpd: (Socket Filtering) are enabled in your kernel
Apr 13 10:32:14 SVR-S02 dhcpd: configuration!
[/HTML]

In all truth, I cannot even begin to fathom what this means, the forums have revealed no useful information and I am at an utter loss as to where to proceed. Any help would be gratefully received.

As an update, I have tried to verify that these modules are being loaded using 
[HTML]grep "CONFIG_PACKET\W" /boot/config- 'uname -r'[/HTML]
this displayed
[HTML]CONFIG_PACKET=y[/HTML]
though the same was not true for CONFIG_FILTER.

lsmod | grep af_packet returned nothing as well.

---

### Post by achaycock on 2009-04-13
OK, I'm not sure of this was the best solution but it has certainly got it working again.

After bashing my head against the wall for a few hours, I figured the kernel had been corrupted, so I tried reinstalling the kernel using
[HTML]apt-get install --reinstall linux-generic[/HTML]
A few minutes later, and I reinitialised the dhcp-server successfully.
[HTML]/etc/init.d/dhcp3-server start[/HTML]

---

