---
title: "Help me please: IP Forwarding + Routing"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by alarrarte on 2009-06-10
Hello everyone. I'm new to this world so please be patient. Here's the thing:

I'm trying to play around with virtual networks (Virtualbox in ubuntu). My computer is connected to a debian server which is my house DHCP Server which is also connected to the ISP and gives me internet access.
This server gives ip addresses 192.168.2.0/24.
Since this has been set up by my brother and i don't want to ruin it I'm trying to set up a virtual network emulating what he did. 1 Virtual Debian server behind my ubuntu OS (2 virtual NICS, 1 bridged to the NIC in which i recieve internet in my Ubuntu OS and then another virtual NIC with internal network to put some XP Hosts and test the debian services).
Then i have eth0 (DHCP to recieve Internet) and eth1 (192.168.3.1 static address, gateway for xp pcs) in my virtual Debian server. The thing is i can access internet from my debian server but my xp test computer is unable to reach internet throught the virtual gateway. I'll put a routing list of my real debian server and my virtual server.

Real debian server:

Destination --------------------------------------- Gateway--------------------Genmask-----------------Iface

192.168.100.2---------------------------------------*----------------------------255.255.255.255-----------tun0
ERMCH03LB1.mrs----------------------------------- *---------------------------- 255.255.255.255-----------ppp0
192.168.100.0---------------------------------------192.168.100.2-------------255.255.255.0-------------tun0
192.168.2.0------------------------------------------*-----------------------------255.255.255.0-------------eth0
default-----------------------------------------------*------------------------------0.0.0.0---------------------ppp0


Virtual Server:

Destination Gateway Genmask Iface

192.168.3.0-------------------------------------------*--------------------------255.255.255.0------------eth1
192.168.2.0-------------------------------------------*--------------------------255.255.255.0------------eth0
default---------------------------------------------192.168.2.1-----------------0.0.0.0--------------------eth0


I also have set up ip forwarding value to 1.

Again, im really new to this so any help would be greatly appreaciated and, if you need any other info or output, please let me know.

Thanks,
Agus.

---

