---
title: "configure Samba Access Point"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by m6a2x6 on 2010-04-27
Hi!

I am desperately trying to install a Wi-Fi Access Point for people to have access to my samba Server.

Hardware:
D-Link DAP-1360
Server with 2 NIC
One to the Switch->LAN->Router
One to the Access Point

Goal is for Wi-Fi user not to access my LAN but only the Samba Server (this is why two NIC)

But I can't seem to get this to work.

Router Adress: 192.168.0.1
AP adress: 192.168.0.50

Here is my etc/network/interfaces:
> auto lo
iface lo inet loopback

#This is for my internet on the server to work
#Seems to be OK since I have working Internet and LAN access from server
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.1
gateway 192.168.0.1

#This is where it becomes problematic
auto eth1
iface eth1 inet static
address 192.168.0.105
netmask 255.255.255.0


Computers connected to the access point can't seem to see the server.

If I Zenmap 192.168.0.* from an AP connected computer, it sees the server but no opened port. (usually 445 ms-ds)

Do you see what I am missing here?

---

