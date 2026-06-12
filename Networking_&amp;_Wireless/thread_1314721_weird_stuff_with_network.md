---
title: "weird stuff with network"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by zeek333 on 2009-11-04
Hi
I'm using BT router, few win2003 servers and few Ubuntu 8.04 servers 2 eth in each server, problem is with one of ubuntu server its changes IP's by it self.
Servers are on DHCP client and BT router is setup as DHCP server,  and its recognise all server host names and IPs. This BT router also let me set this particular server IP as fixed IP, but it doesn't work with only one server when I set these IP's after moment its changes IP to something else. eg 
after insall i set in router IPs eth0 192.168.1.100 and eth1 10.10.10.1 (ext IP) but after few moments when i checked router its didnt recognise one of eth. after network restart its assign new IPs eth0 10.0.0.2 and eth1 10.0.0.3 

New devices added to BT should should assign internal IP 192.168.1.X but that server both eth changes to ext IP

Server is fresh ilstalled version.

Thank you.

---

### Post by zeek333 on 2009-11-08
never mind it was an network card driver issue.

---

