---
title: "Not able to connect wireless"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by texas.chef94 on 2009-03-06
I am reposting this netgear WG511T concern with as much information as I can possibly produce with my limited wireless knowledge. This compaq is connected to no router and only has Ubuntu 8.10 with no other OS. In support of the wireless card the owner previously had windows and was connected wireless.
I am only reposting in desperation so please excuse any list breached protocols
I tried the following in the terminal
giff@giff-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:8a:0c:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB) 

giff@giff-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 


giff@giff-laptop:~$ network-admin 
The program 'network-admin' is currently not installed.  You can install it by typing: 
sudo apt-get install gnome-network-admin 
bash: network-admin: command not found 
SO I TRIED TO INSTALL
giff@giff-laptop:~$ sudo apt-get install gnome-network-admin 
[sudo] password for giff: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
E: Couldn't find package gnome-network-admin 

Tried dhclient 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
SIOCSIFADDR: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFADDR: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFFLAGS: Permission denied 
Open a socket for LPF: Operation not permitted 
SO I TRIED TO FORCE INTERFACE
using Ethernet adapter local are connection as well as  the one listed under the PPP adapter
(E65F2985-E3F6-42E1—82C6-3360C2040978)
So you see I really am groping
 sudo ifconfig eth1 192.168.0.2 
SIOCSIFADDR: No such device 
eth1: ERROR while getting interface flags: No such device 
 sudo ifconfig eth1 172.162.242.102 
SIOCSIFADDR: No such device 
eth1: ERROR while getting interface flags: No such device

---

### Post by N04h on 2009-03-06
Try sudo dhclient instead.

---

