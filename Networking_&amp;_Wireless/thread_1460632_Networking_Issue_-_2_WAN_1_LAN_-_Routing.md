---
title: "Networking Issue - 2 WAN 1 LAN - Routing"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by Griftor on 2010-04-23
Hi All

I am having some trouble setting up routing on my Ubuntu 9.10 Server. I  have the GUI installed with Webmin and OpenVPN
Heres the setup :

1 NIC - WAN - eth0 - IP: 146.231.x.x SUBNET: 255.255.252.0
1 NIC - LAN - eth1 - IP: 192.168.1.1 SUBNET: 255.255.255.0
1 NIC - ADSL - eth2 - dynamic

What I need to do is the following.

All users are connected to the LAN.

All requests for IP range "146.231.x.x", and "domain.com" need to be  routed from LAN (eth1) to WAN (eth0).

All other internet requests need to be routed to ADSL (eth2).

-> I have the masquerading in the linux firewall working for NAT, but  all traffic goes to ADSL (eth2).
-> I am using OPEN-VPN over the ADSL also.
-> DHCP and DNS work fine.


I also need all ports opened with the route (from eth1 to eth0)

Please can anyone offer advice or a solution on how to get this working.

Thanks in advance!

---

