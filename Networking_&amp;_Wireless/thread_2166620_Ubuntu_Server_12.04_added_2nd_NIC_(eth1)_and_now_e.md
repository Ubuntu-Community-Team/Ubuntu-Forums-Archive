---
title: "Ubuntu Server 12.04 added 2nd NIC (eth1) and now eth0 will not receive updates"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by phoenix32 on 2013-08-10
I've been using Ubuntu for a few years and I recently decided to build a server.  I used the onboard NIC on the motherboard as eth0, and then added a second NIC as eth1.  Once I edited the /etc/network/interfaces file to include eth1, my server will not reach beyond my LAN.  I could use a hand, please!  Thank you. : )

---

### Post by Linux90s on 2013-08-10
you'll have to explain your setup a little bit more...

post your /etc/network/interfaces file

detail the subnets each card uses if they are different, are you using one static and one dhcp? both static or both dhcp?

what does the command:

route

give you?

post this info and someone should be able to help

---

### Post by papibe on 2013-08-10
Hi phoenix32.

Just like the naming of disk devices, the system names the network devices. My first guess is that they were named the other way around.

Check this by running:
```
sudo lshw -C network
```
Each interface should have a like like this (with the device name assigned):
```
logical name: eth0
```
Let us know how it goes.
Regards.

---

### Post by phoenix32 on 2013-08-10
A little extra background... I installed Ubuntu Server with the onboard  NIC (eth0) and then added the PCI NIC (eth1) after I had set up the  server the way I wanted it (more or less).

Both are DHCP.  I have a WAN and LAN that are separate (too many reasons to list!).

My /etc/network/interfaces reads as follows:

# The loopback network interface
auto lo
iface lo inet loopback

# The Primary network interface
auto eth0
iface eth0 inet dhcp

# The Secondary network interface
auto eth1
iface eth1 inet dhcp

When I type "route" it reads as follows:

Kernel IP routing table
Destination      Gateway      Genmask          Flags     Metric     Ref       Use Iface
default            78.81.82.88 0.0.0.0              UG        100        0            0 eth1
78.81.82.88     *                255.255.255.0   U           0           0            0 eth1
192.168.1.0     *                255.255.255.0   U           0           0            0 eth0

I want eth0 (which is the WAN) to be the default, and I am guessing by the output that eth1 (which is the LAN) is the default.

The output from "sudo lshw -C network" is considerable, but it looks to me like "network:0" is the added in card, eth1, and "network:1" is the onboard NIC built into the motherboard (eth0).

Thanks for the prompt responses-- one of the things I love about being a part of this community! : )

---

