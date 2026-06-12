---
title: "how do i setup ubuntu home network"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by dannyz on 2009-09-10
i found a tutorial which shows how to setup ubuntu server as a router and i have it working but my ubuntu server has 3 ethernet ports one plugs directly into the cable modem and the other into my windows Pc via crossover cable and i can access the internet on both machines 

my problem is when i try adding another crossover cable in the 3rd port to my laptop i cannot access the internet now i know that i could use a switch on the second ethernet port but it would be pointless because i only want to connect one more Pc to the network so i thought of using a crossover cable in the 3rd ethernet port instead but i can't get it to work does anyone know if its possible in ubuntu ?

because i know it is easy done on windows via bridging 2 connections together while the 3rd plugs directly into the cable modem

thanks in advance

---

### Post by dannyz on 2009-09-10
this is the link to the tutorial i followed [http://server-servers.com/ubuntu-internet-gateway-and-router/](http://server-servers.com/ubuntu-internet-gateway-and-router/)

do i need to create a network bridge between eth1 and eth2 ? :confused:

---

### Post by dannyz on 2009-09-10
anyone ? :confused:

---

### Post by Iowan on 2009-09-10
[Here]("http://wiki.openzaurus.org/HowTos/Bridging_with_Ubuntu") is a bridging How-To, but it would seem that some (more) iptables rules should make Ubuntu act as a switch/router. Perhaps something in this [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page will be useful.

---

### Post by dannyz on 2009-09-11
which ethernet ports do i need to bridge ? heres my setup 

[CENTER]   internet
         |
   modem
         |
         |
     eth0 <=== gets ip via dhcp
--------------
ubuntu/router
--------------
 eth1    eth2
     |         | 
     |         |
  Pc1     Pc2
[/CENTER]
 
i can only access the internet on Pc1 using crossover cable but i want Pc2 to access the internet heres my network interfaces settings
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet static
address 192.168.10.1
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
bridge_ports eth1 eth2
bridge_maxwait 0
```:confused:

---

### Post by machesked on 2009-09-30
In the guide i wrote, it was meant eth0 for your internet address and eth1 for your local network address.  Following the setup, you will create the router or bridge he internet connection with your local network by setting up the firewall definitions further in the guide.

---

### Post by machesked on 2009-09-30
> **dannyz said:**
> which ethernet ports do i need to bridge ? heres my setup 

[CENTER]   internet
         |
   modem
         |
         |
     eth0 <=== gets ip via dhcp
--------------
ubuntu/router
--------------
 eth1    eth2
     |         | 
     |         |
  Pc1     Pc2
[/CENTER]
 
i can only access the internet on Pc1 using crossover cable but i want Pc2 to access the internet heres my network interfaces settings
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet static
address 192.168.10.1
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
bridge_ports eth1 eth2
bridge_maxwait 0
```:confused:

I would just buy a switch and hook it to one ethernet connection.  The only cost $30

---

