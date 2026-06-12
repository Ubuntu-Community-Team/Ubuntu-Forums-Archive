---
title: "Add multiple Dynamic IPs with ifconfig?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by DaRabman on 2009-05-18
Hey,
I'm trying to establish a range of internal IPs for my NIC, I can easily add and save static IPs using ifconfig, but after a bit of tinkering I've still had no luck with adding dynamic IPs, allowing me to retain DHCP on my LAN.
Is this even possible? I'm on Jaunty Server 9.04, so no GUIs plz.

DaRab.

---

### Post by superprash2003 on 2009-05-19
you mean , eth0 and eth0:0 , that way right?? if so , in your /etc/network/interfaces file , specify each one of them  , and for dhcp interfaces use the inet dhcp line

---

### Post by DaRabman on 2009-05-19
Here's the entry for my /etc/network/interfaces file:
```

auto lo
iface lo inet loopback

auto eth0
auto eth1

iface eth1 inet dhcp
iface eth1:0 inet dhcp

```
(Note that eth0 is my second physical network adapter that I'm not using)

Is this syntax correct? I've tried restarting **/etc/init.d/networking** and checking with ifconfig, but it only shows the profile for the original eth1 profile.

I tried:
```
darab@DaRack:~/srcds_g$ sudo ifup eth1:0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Bind socket to interface: No such device
Failed to bring up eth1:0.
```

But to no avail, any ideas/corrections?
Sam

---

### Post by superprash2003 on 2009-05-20
try adding the line

auto eth1:0

---

### Post by dmizer on 2009-05-20
What are you trying to acomplish by doing this? Are both network cards connected to the same router? If not, are both routers on different subnets?

---

### Post by DaRabman on 2009-05-20
eth0 represents a physical network adapter and is redundant (namely because it isn't plugged in). eth1 represents my second physical network adapter (that is, there are two adapters in the one machine) and is connected to one router that serves as my internet gateway and the DHCP server.
I'm looking to establish multiple local IPs on the eth1 interface (eth1:0, eth1:1, etc. etc.) but I want the IPs to be assigned by DHCP rather than using manual configuration. The reason that I'm not simply using both interfaces for seperate addresses is because ideally I need at least three seperate IP addresses.

---

### Post by dmizer on 2009-05-20
Sorry, what you are doing is not really possible. You can't have two routeable IP addresses assigned by the same DHCP server. How will Ubuntu know which ethernet card to send traffic on?

It is possible to create a failover for the network cards, but this will have no effect on speed or traffic volume capability.

Edit:
For what reason would you need three local IP addresses?

---

### Post by DaRabman on 2009-05-20
> **dmizer said:**
> 
For what reason would you need three local IP addresses?
At the risk of losing some credibility(!), I'm hosting gameservers for an upcoming LAN party, I'm running the same binary several times and would rather specify seperate IPs for each server binary than having to awkwardly specify ports for each of them (considering the game's client/server data, amongst other things is sent through a range of ports, not simply one each).

I find it difficult to understand how several static IPs can be set manually for each interface, yet allowing these IPs to be established automatically by DHCP is effectively impossible? Is there not an alternative method like a Virtual machine or network that would allow my server machine to receive data on a number of addresses (established dynamically)?

Ta,
Sam.

---

### Post by dmizer on 2009-05-20
The difference between DHCP and static is where the traffic is controlled. With static IP addresses, your sever is the host. Clients connect directly to the server in this case, and both client and server are explicitly told which IP (and therefore which network card) to use. With DHCP, the router is the host, and clients connect to the server indirectly through the DHCP server. In this case, the client, router, and server have no idea which IP or network adapter to use so the network crashes.

As you guessed, Virtual machines could do what you want.

---

### Post by DaRabman on 2009-05-21
> **dmizer said:**
> As you guessed, Virtual machines could do what you want.

I can't say that I know how to start with virtul machines, what's the exact principle behind them and how could i get them to do what I want?

Darab.

---

### Post by DGortze380 on 2009-05-21
> **dmizer said:**
> Sorry, what you are doing is not really possible. You can't have two routeable IP addresses assigned by the same DHCP server. How will Ubuntu know which ethernet card to send traffic on?


Why is this misconception so prevalent on these forums?

You can have as many IP Addresses as you like on a single machine DHCP or otherwise. You'll likely need to add static routes to get everything moving correctly though.

---

### Post by DGortze380 on 2009-05-21
> **dmizer said:**
> The difference between DHCP and static is where the traffic is controlled. With static IP addresses, your sever is the host. Clients connect directly to the server in this case, and both client and server are explicitly told which IP (and therefore which network card) to use. With DHCP, the router is the host, and clients connect to the server indirectly through the DHCP server. In this case, the client, router, and server have no idea which IP or network adapter to use so the network crashes.

As you guessed, Virtual machines could do what you want.

I fear you're incorrect...

Traffic does NOT route through a DHCP Server. The DHCP Server hands down IP Address, Subnet, Gateway, and DNS. Once the host has this information, traffic is routed as in any other IPv4 network.

---

### Post by dmizer on 2009-05-21
Misconception is common everywhere.

> **DGortze380 said:**
> You can have as many IP Addresses as you like on a single machine DHCP or otherwise. You'll likely need to add static routes to get everything moving correctly though.

Well, if this is true, I'm more than willing to be corrected. I've just always understood that you can't have more than one adapter connected to the same subnet unless you have a static network.

Please explain how this is accomplished.

---

### Post by DGortze380 on 2009-05-21
> **dmizer said:**
> Misconception is common everywhere.



Well, if this is true, I'm more than willing to be corrected. I've just always understood that you can't have more than one adapter connected to the same subnet unless you have a static network.

Please explain how this is accomplished.

Certainly.

It is easier with static addresses, but.. so long as each NIC has a unique IP, regardless of Static or DHCP, traffic can be routed correctly, even on the same subnet. 

The trick is the static routes. You are certainly limited in how configurable these routes may be with dynamic address. 

The simplest solution is to use a default route through a particular interface. Any special traffic, from a VM for example, would then need a separate route through the other interface. You'll need to specify an interface for all traffic, otherwise it uses the default route.

The real problem is getting traffic out through the correct interface. Once the packet is out, it has the correct IP, of the correct interface, and all traffic will be routed back to the same interface.

---

