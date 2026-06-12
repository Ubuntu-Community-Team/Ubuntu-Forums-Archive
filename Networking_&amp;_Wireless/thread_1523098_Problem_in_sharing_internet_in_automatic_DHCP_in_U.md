---
title: "Problem in sharing internet in automatic DHCP in UBUNTU"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by najeebmankada on 2010-07-03
I working in an University Computer Centre
we have a problem in configuring  Automatic DHCP for INTERNET sharing
can anybody help me

Our public IP is 117.240.231.233
DNS    	218.248.240.23 and 218.248.240.135 	 	 	 	  desired dhcp ip range is 192.168.1.10 to 240

ip for dhcp server is 192.168.1.1

 _Steps that i have done_
installed dhcp3
  	 	 	 	 	 	  
changes made in /etc/default/dhcp3-server
INTERFACES=”eth1&#8243; 
Edited /etc/dhcp3/dhcpd.conf file 
   	 	 	 	 	 	  default-lease-time 600;
max-lease-time 7200;
 option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 218.248.240.23, 218.248.240.135;
option domain-name “”;
 subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.240;
}
-----------------------------

 
 automatic dhcp is working in clients
but there is trouble in getting internet
pl help me to configure the same

---

### Post by Iowan on 2010-07-03
What is at 192.168.1.254? My DHCP server is not the router, so I have the default router set to 192.168.1.1 (my modem). Checking **route -n** on this client machine shows 192.168.1.1 as the default route.

---

