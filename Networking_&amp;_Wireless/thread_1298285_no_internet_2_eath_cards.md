---
title: "no internet 2 eath cards"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by curtisc225 on 2009-10-22
I had this working last night I updated the box and now i have no internet connection.

jaunty jackalope kernal 2.6.28-16-server 
This system has two network cards, each connecting to the same physical network. All two cards work fine

eth0 no internet 
eth1 no internet 

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.75
netmask 255.255.255.0
gateway 192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.0.77
netmask 255.255.255.0
gateway 192.168.0.1


```

route

192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         home            0.0.0.0         UG    100    0        0 eth1
default         home            0.0.0.0         UG    100    0        0 eth0

---

### Post by Iowan on 2009-10-22
Two network cards in the same subnet should confuse the machine - are you using [bonding]("https://help.ubuntu.com/community/UbuntuBonding")?

---

### Post by curtisc225 on 2009-10-23
No I can't bind my nics. I'm setting up vpn and dns.

---

### Post by shairozan on 2009-10-23
I'm just curious as to why you have two NICs on the same network. Either immediately or over time you're going to have asynchronous routing issues where the machine will be unsure which route to deliver through. 

I had a similar problem I had to work with when running NTOP and Opsview on a single server. One NIC was plugged into a mirrored port to scan all traffic running through the switch network. The other was just used to poll against the network. The problem is I could never discern DNS information from NTOP's mirrored port if it didn't have an address on the same subnet. I ended up having to abandon NTOP because, over time, the machine would start "losing visibility" to the network throwing errors in Opsview. It was just sending everything out of the wrong NIC. 

Also what kind of VPN are you looking at setting up? I assume you're setting up a bind server for DNS.

---

### Post by curtisc225 on 2009-10-23
I'm going to Collage and my school blocks most of the sights I need to go to for class or want to go to. I'm just going to by pass them and vpn to my house and use it's connection to go where i need or want to.  Yes I'm going to use binds and openvpn for the vpn.

---

