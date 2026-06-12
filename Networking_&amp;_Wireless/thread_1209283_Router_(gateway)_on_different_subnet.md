---
title: "Router (gateway) on different subnet"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by ttheron on 2009-07-10
Hi all,

I am fairly new to Linux and trying to set up a LAMPS server to connect via the company router. The network looks like this:

Ubuntu LAMPS Server
IP address: 192.168.11.1
|
|
Gateway (Cisco Router) Ip address: 192.168.10.3
|
|
Windows Server (DNS Server) 192.168.10.10

I know many would say it is not the right thing to use two subnets, but that is just the way the network is set up and I have to live with it. 

My setup on Ubuntu as below:

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:23:54:6f:64:0b  
          inet addr:192.168.11.1  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe6f:640b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1213383 (1.2 MB)  TX bytes:177610 (177.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1093752 (1.0 MB)  TX bytes:1093752 (1.0 MB)

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.3    0.0.0.0         UG    0      0        0 eth0

interface file:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.11.1
    netmask 255.255.254.0
    network 192.168.11.0
    broadcast 192.168.11.255
    gateway 192.168.10.3

I have also executed 
  route add -host 192.168.10.3 eth0
  route add default gw 192.168.10.3 eth0
as per many suggestions I found by browsing, but to no avail.

I cannot ping the gateway at all.

Any suggestions on where I am still going wrong? 

Thanks
Tom

---

### Post by superprash2003 on 2009-07-10
i dont think that would work that way.. you would need to setup an ip of the form 192.168.10.x

---

### Post by ttheron on 2009-07-12
Looking at the following discussion it seems possible, but it doesn't work for me.


[http://www.unixresources.net/linux/lf/58/archive/00/00/17/61/176142.html](http://www.unixresources.net/linux/lf/58/archive/00/00/17/61/176142.html)


Tom

---

### Post by Iowan on 2009-07-12
What the link appears to have done was change the subnet mask to put both addresses in the same subnet.  I don't have access to my handy subnet calculator, but I suspect you need a few more bits in the local net.

---

### Post by ttheron on 2009-07-14
I've spoken to our network manager, and seems the router is not correctly set up to do NAT/PAT from the x.x.10.x to x.x.11.x network. Once they fixed that, I'll be able to configure my  gateway setting to an x.x.11.x gateway, as the router will then present as a x.x.11.x VLAN.

Thanks for your input.

---

