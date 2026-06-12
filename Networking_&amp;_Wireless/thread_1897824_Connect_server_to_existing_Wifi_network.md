---
title: "Connect server to existing Wifi network"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by Yumi on 2011-12-20
I have a home network with a Wifi router (DHCP server) to share the internet access.
To enlarge my network I installed Ubuntu Server 10.10 on a Desktop Machine. Now I try to connect the server to the existing network but face problems.

Server is set to static IP 192.168.0.50, other network is on DHCP

I followed some guides but:

ifconfig -a | grep network
[COLOR="Red"]eth[/COLOR]0  Link encap:Ethernet HWaddr 

lshw -class network
no results show up

I can not see the server from the client computer.

Any advice?

Michael

---

### Post by Yumi on 2011-12-20
I do not know why, but the card was working and it is now connected.

The present configuration is that the wireless router has the DHCP server on and is set to issue always the same IP 192.168.0.150 to the MAC address of the server. The new server is linked to it by wire. The servers is set to DHCP, a change from static as in my previous post. 

Another, unrelated issue I encountered. After installing Ubuntu server 11.10 the file /etc/apt/sources.list was empty. I tried to install webmin but the required depentency libnet-ssleay-perl could not be found and installed.

I looked at the sources.list file on my laptop (also 11.10) and manually wrote the lines into the servers sources.list. Voila - suddenly the server found all the dependencies and installed webmin.

Michael

---

