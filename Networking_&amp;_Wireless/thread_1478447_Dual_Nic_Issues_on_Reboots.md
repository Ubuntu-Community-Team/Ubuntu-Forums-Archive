---
title: "Dual Nic Issues on Reboots"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by rabbit20 on 2010-05-09
Update: 
Updated the server and rebooted it and it looks to be fixed. My shares came back, and I am able to access the server shares. VNC is having some isseus now but im sure I can figure them out. 

Here is my Setup. 
I have a server for backups and Network Files. My desktop is directly connected to the server via a cross over cable. The IPs on the server are static. 

The Nics are setup through the file /etc/network/interfaces 

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback 

#The primary network interface 
iface eth0 inet static
address 192.168.1.18
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

iface eth1 inet static 
address 192.168.2.1
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255

I had eth0 on dhcp but I would lose internet connection on the server when eth1 was up. eth1 is the cross over connection. When is set it to static I was able to access the internet. I set the gateway on eth1 to the ip of eth0 since eth0 is the connection to the switch. 

The issue is that when I reboot the desktop the server will lose its IP address on eth1 (the cross over connection) Any ideas? I also noticed that the loop back is using both nics. Is that ok?

---

