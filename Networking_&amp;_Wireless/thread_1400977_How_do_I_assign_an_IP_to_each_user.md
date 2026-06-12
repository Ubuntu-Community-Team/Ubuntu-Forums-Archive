---
title: "How do I assign an IP to each user?"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by MusicalMind on 2010-02-07
Hello,
 
I have a server with six IP addresses and I have six users. I wish for each to receive a unique IP.
 
I have:
 
iface eth0 inet static
address 212.x.x.100
netmask 255.255.255.0
gateway 212.x.x.1
 
iface eth0:0 inet static
address 212.x.x.101
netmask 255.255.255.0
gateway 212.x.x.1
 
.
.
.
 
iface eth0:5 inet 
address 212.x.x.106
netmask 255.255.255.0
gateway 212.x.x.1
 
All working and showing in ifconfig.
 
So how do I assign user 1 to the first, user 2 to the second .. etc.
 
Thanks

---

### Post by janungh on 2010-03-10
Hi,

I have the same issue, can anyone help here, please.

thanks..

---

### Post by Iowan on 2010-03-10
.100 - 106 is 7 addresses, but...
Is the server issuing addresses (DHCP) - or is it a "community workstation"? Is it a "server-install" (no desktop) or does it have Network Manager?

---

### Post by zaphod777 on 2010-03-10
Assuming that each user is trying to use the same server that has 6 ip address and when they login you want them to each have a different ip address. Is not exactly possible per say.

All out bound communication will go out the ip that has the default gateway. 

what you could do is install vmware server or xen or something like that on the base os and then install a separate server for each user with a different ip address.

or i guess you could possibly write a login script for each user that will shutdown all interfaces and bring up the one with the ip you want them to have. I guess that could probably work but I am not sure why you would really want to do this. 

If this is for web pages then you can assign a specific url or ip address to a specific virtual site in apache.

---

