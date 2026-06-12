---
title: "Unable to run 2 ethernet connections at the same time"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by FHDumay on 2010-03-07
L.S.;

I am a bit puzzled; i have a workstation with the two ethernet ports (eth0, eth1), the problem is that i cannot run with both ports up and running. I can run with either one of them, but not both. Searching on the internet has not given me anything that made sense to me, so maybe someone here can point me in the right direction. 

Below is the contents of my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address     192.168.1.200
netmask     255.255.252.0
gateway     192.168.1.1

dns-nameservers    212.54.40.25 212.54.35.25

#auto eth1
iface eth1 inet static
address     192.168.1.201
netmask     255.255.252.0
gateway     192.168.1.
```Short description of my config;

Tyan 5396 Mainboard (intel 5400 chipset), with the QuadCore Xeon CPU's, 16GB RAM, RocketRaid Raid Controller with 8 x 500 GB storage attached.

0f:00.0 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
0f:00.1 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01

Running on 64 bit Ubuntu 9.10 Desktop

---

### Post by Iowan on 2010-03-07
Have you tried it with the interfaces in different subnets? (Also, you'll want only one gateway...)

---

### Post by DGortze380 on 2010-03-07
> **FHDumay said:**
> L.S.;

I am a bit puzzled; i have a workstation with the two ethernet ports (eth0, eth1), the problem is that i cannot run with both ports up and running. I can run with either one of them, but not both. Searching on the internet has not given me anything that made sense to me, so maybe someone here can point me in the right direction. 

Below is the contents of my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address     192.168.1.200
netmask     255.255.252.0
gateway     192.168.1.1

dns-nameservers    212.54.40.25 212.54.35.25

#auto eth1
iface eth1 inet static
address     192.168.1.201
netmask     255.255.252.0
gateway     192.168.1.
```Short description of my config;

Tyan 5396 Mainboard (intel 5400 chipset), with the QuadCore Xeon CPU's, 16GB RAM, RocketRaid Raid Controller with 8 x 500 GB storage attached.

0f:00.0 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
0f:00.1 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01

Running on 64 bit Ubuntu 9.10 Desktop

That's because they're on the same subnet.

Why do you want to use both NICs? That will greatly influence your solution.

Start here: [https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

---

### Post by Charly85551 on 2010-03-08
Why would you like to use 2 network interfaces to the same network? The TCP/IP protocol does not allow parallel connections in one network because you may get conflicting messages sent to the same IP. 
I have built quite a few PC's as servers with 2 installed network cards because I wanted one internal network  (15 PC's) communicating to one port in a certain subnet and my server software then decided if internet access was allowed or not (so-called proxy function) in a different subnet. This way I was able to run timetables and iptables (=firewalls) at the same time. The router was then connected to this 2nd subnet.
Hope this helps. Details are defined in IEEE 802.3.
cheers
Charly85551

---

### Post by zaphod777 on 2010-03-08
> **Charly85551 said:**
> Why would you like to use 2 network interfaces to the same network? The TCP/IP protocol does not allow parallel connections in one network because you may get conflicting messages sent to the same IP. 
I have built quite a few PC's as servers with 2 installed network cards because I wanted one internal network  (15 PC's) communicating to one port in a certain subnet and my server software then decided if internet access was allowed or not (so-called proxy function) in a different subnet. This way I was able to run timetables and iptables (=firewalls) at the same time. The router was then connected to this 2nd subnet.
Hope this helps. Details are defined in IEEE 802.3.
cheers
Charly85551
The link that DGortze380 provided should show you how to do it. 

There are certain situations when you would want to do this mainly on servers so you have a connection that is load balanced or redundant so if one connection goes down then the server still maintains it's connection.

At my old work we had servers like our main file server serving the whole campus that has 2 NICS one going to each of our core CISCO switches (CISCO 6509 series). The 2 NICS are bonded to be 1 virtual NIC so if we lose a NIC then users won't notice. Or god forbid we lose a core switch the users not going through that switch can still access the file server. 

At home the only reason I could think that you would want to do this is to maybe get better performance but if you have 100mb NICS you would need a gigabit switch to get any performance gains. Also unless you have some sort of RAID array I am not sure if you could even write to the disk fast enough to make a difference anyway.

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

