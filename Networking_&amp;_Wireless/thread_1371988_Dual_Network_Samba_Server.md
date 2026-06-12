---
title: "Dual Network Samba Server"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by rush.evan on 2010-01-04
I have a Server setup for DHCP and Samba Sharing. There are 2 NICs in the server on 2 different subnets. For the network connected to eth1 all users can see the Server and connect to it via "Networks" in Windows but... for the network connected to eth0 the users cannot see the server but can connect to it via \\"ip address". This would be acceptable to me in a small network but this is a large network I need this server to be visible. Also the server is only a DHCP server on eth0, but I have turned off DHCP and added a router into the mix to take over DHCP just to see if the DHCP on the server was the issue, but it hasnt changed anything. In both setups I can still access it via \\"ip address". 
 
Why is the server not visible on eth0 but visible on eth1?
 
Using 9.10 x64 Desktop

---

### Post by rush.evan on 2010-01-04
*Solved* all settings were configured properly, a reinstall of winbind fixed it

---

### Post by Iowan on 2010-01-04
Glad you got it fixed. You can mark the thread solved by using the option under Thread Tools. :)

---

