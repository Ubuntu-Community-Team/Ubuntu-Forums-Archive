---
title: "Problem with Dual NICs and Internet + DRBL + PXE"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by cniehoff on 2009-01-27
I started a post but cannot find it now so i will try again.  I have a 8.10 server box that has two nics eth0 is static set and is were my internet comes from. eth1 is my DCHP server and also my PXE connection.  The problem i am having is that when i boot up my server i will have to ipconfig eth1 down and then go to a website and then bring up the eth1 connection.  AFter that my internet works on the server and the workstations connected to eth1.  Here is some of the configuration.

sudo /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.98.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.98.1    0.0.0.0         UG    100    0        0 eth0

sudo /etc/network/interfaces

auto lo
iface lo inet loopback


 auto eth0
# iface eth0 inet dhcp
 iface eth0 inet static
 address 192.168.98.151
 netmask 255.255.254.0
 gateway 192.168.98.1
 network 192.168.98.0
 broadcast 192.168.98.255


 auto eth1
 iface eth1 inet static
 address 192.168.0.1
 netmask 255.255.255.0
 gateway 192.168.0.1
 network 192.168.0.0
 broadcast 192.168.0.255

---

