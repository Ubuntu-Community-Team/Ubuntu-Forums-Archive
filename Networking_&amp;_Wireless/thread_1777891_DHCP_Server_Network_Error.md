---
title: "DHCP Server Network Error"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by jjleonb on 2011-06-08
Hi, I've installed the dhcp3 server in order to assign DHCP to a Windows Desktop, here are the facts:

I'm connecting via wireless through the router (Telephone Company), with this connection everything is working properly, but I've another PC (Windows XP Desktop), so I want that this one belongs to a network  different  that I have with the wireless connection.  I'm using the wired connection connected to a switch (both of them).  I want to create (first of all) a DHCP connection from my ubuntu server to assign IP's dynamically to every host that connects to that switch, and after this use my Ubuntu server to be a Proxy.  But when I Configured the wired connection in the syslog presents that i have to define the subnet network, and I already did it.  here is my configuration on both of them.  As I said before my wireless connection (internet) is working perfect.  

Wan0
address 192.168.1.15
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

eth0
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.1
broadcast 10.0.0.255
network 10.0.0.0

this one goes in /etc/dhcp3/dhcpd.conf
Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 10.0.0.255;
option routers 10.0.0.1;
option domain-name-servers 10.0.0.1;
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.10 10.0.0.20;

}
and I have my eth0 listening in /etc/default/dhcp3-server by default

---

### Post by jjleonb on 2011-06-11
Hi, Any help would be greatly appreciated... I'm still waiting for some kind of help in this service... At least how the dhcp server works properly...

---

### Post by Iowan on 2011-06-11
It's been awhile since I worked with DHCP3 server (I changed to DNSMASQ). The gateway is the port to which all "non-local" traffic should go - so only one interface should have one defined - and it should point to the next "upstream" machine - not to itself.

... or I'm mis-remembering things :(

---

### Post by jjleonb on 2011-06-12
Thanks a lot, that was the configuration error that I had, when I changed the pool and the manual configuration of my wired connection, it really worked.

---

