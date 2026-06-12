---
title: "Virtual network setup troubles"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by onthatday7yearsago on 2010-05-17
Hello, I'm trying to set up some virtual network cards in my Ubuntu 8.04 VM (I need python 2.5 as default) and I'm having some trouble with the virtual cards. My regular connectivity is fine, the standard eth0 can hit the internet and all of the virtual cards without any issues. My problem is that the virtual cards won't talk to anything. I can ping them fine from the standard address, but all tracert or ping -I from the virtual interfaces results in Destination Host Unreachable errors. All I really need is for vlan2/3 to be able to ping each other, I feel that I must have misconfigured something somewhere.

Routing table:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.171.0   *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 vlan2
192.168.0.0     *               255.255.0.0     U         0 0          0 vlan2
192.168.0.0     *               255.255.0.0     U         0 0          0 vlan3
default         192.168.171.2   0.0.0.0         UG        0 0          0 eth0


My /etc/network/interfaces is as follows:

auto lo
iface lo inet loopback

auto vlan2
auto vlan3

# VLAN 2
iface vlan2 inet static
address 192.168.2.2
netmask 255.255.0.0
network 192.168.2.0
broadcast 192.168.2.255
mtu 1500
vlan_raw_device eth0

# VLAN 3
iface vlan3 inet static
address 192.168.3.3
netmask 255.255.0.0
network 192.168.3.0
broadcast 192.168.3.255
mtu 1500
vlan_raw_device eth0

ifconfig for goog measure:
eth0      Link encap:Ethernet  HWaddr 00:0c:29:62:ac:34  
          inet addr:192.168.171.134  Bcast:192.168.171.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe62:ac34/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127295 (124.3 KB)  TX bytes:168470 (164.5 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83108 (81.1 KB)  TX bytes:83108 (81.1 KB)

vlan2     Link encap:Ethernet  HWaddr 00:0c:29:62:ac:34  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.0.0
          inet6 addr: fe80::20c:29ff:fe62:ac34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:3921 (3.8 KB)

vlan3     Link encap:Ethernet  HWaddr 00:0c:29:62:ac:34  
          inet addr:192.168.3.3  Bcast:192.168.3.255  Mask:255.255.0.0
          inet6 addr: fe80::20c:29ff:fe62:ac34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:4913 (4.7 KB)

IPtables

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

Any thoughts?

Thanks.

---

