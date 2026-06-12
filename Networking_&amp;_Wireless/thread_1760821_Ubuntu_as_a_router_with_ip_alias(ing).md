---
title: "Ubuntu as a router with ip alias(ing)"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by stomp442 on 2011-05-17
I need to set up Ubuntu to act as a layer 3 device, routing packets between student networks.

There are eight total networks. Each network consists of a firewall, server and workstation. The networks are entirely virtual, except for the public facing interface on the firewall.

My solution was to setup Ubuntu Server 10.10 with one interface and then alias the interface so that each interface will act as the gateway for those public facing interfaces on the firewalls.

FW1 > IP Alias GW1 > Ubuntu Server > IP Alias GW2 > FW2

FW1:
172.25.105.1/30 gateway is 172.25.105.2

FW2:
172.26.106.1/30 gateway 172.26.106.2

IP Alias GW1
172.25.105.2/30

IP Alias GW2
172.26.106.2/30

At present, I have set up two aliases without issue. Enabled ip_forwarding and proxy arps (more on that in a sec).

If FW1 send a ping to its gateway it receives a response. If it sends to the gateway for FW2, it receives a response. If FW1 tries to send a ping directly to FW2, no response.

Figuring that I am an idiot, I used tcpdump and observed that those pings traverse the interfaces .105.2 to 106.2, but never receive a response. Only requests.

Checked the arp table, and found that the only entries are for the GWs, not the firewalls.

Checked the routes, and found that there are routes to each of the FWs.

To complicate further, I can sit on the Ubuntu box and send pings successfully to each of the FWs, successfully.

I know I'm missing something obvious. :confused:

Help would be greatly appreciated.

---

### Post by stomp442 on 2011-05-18
No one wanna bite on this?

bump

---

### Post by lz1dsb on 2011-05-19
Could you show to us the content of the file /etc/network/interfaces and the output of the command route -n?
If I get it right, the Ubuntu server is expected to perform routing between two networks, right?

---

### Post by stomp442 on 2011-05-19
Unfortunately, I'm in class right now. No access to the lab that I have set up.

I will get the netstat and interface information. Do you want a copy of the arp entries?

Stomp442

---

### Post by lz1dsb on 2011-05-19
The more information you provide, the better :D

---

### Post by stomp442 on 2011-05-19
instructor@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.20.100.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
172.26.106.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
172.25.105.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG        0 0          0 eth1


instructor@ubuntu:~$ arp -a
? (192.168.10.200) at 6c:f0:49:4f:47:8f [ether] on eth1
? (192.168.10.2) at 00:1d:73:b3:2c:1e [ether] on eth1
? (192.168.10.1) at 00:06:4f:66:0f:b1 [ether] on eth1


instructor@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:24:bf:99  
          inet addr:172.20.100.2  Bcast:172.20.100.3  Mask:255.255.255.252
          inet6 addr: fe80::20c:29ff:fe24:bf99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11920 (11.9 KB)  TX bytes:468 (468.0 B)

eth0:105  Link encap:Ethernet  HWaddr 00:0c:29:24:bf:99  
          inet addr:172.25.105.2  Bcast:172.25.105.3  Mask:255.255.255.252
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:106  Link encap:Ethernet  HWaddr 00:0c:29:24:bf:99  
          inet addr:172.26.106.2  Bcast:172.26.106.3  Mask:255.255.255.252
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:0c:29:24:bf:a3  
          inet addr:192.168.10.225  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe24:bfa3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38095 (38.0 KB)  TX bytes:21112 (21.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


instructor@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

# Primary Check Point Lab interface
auto eth0
iface eth0 inet static
name 100-Net
address 172.20.100.2
netmask 255.255.255.252
broadcast 172.20.100.3
network 172.20.100.0

# Check Point 105 network (alias)
auto eth0:105
iface eth0:105 inet static
name 105-Net
address 172.25.105.2
netmask 255.255.255.252
broadcast 172.25.105.3
network 172.25.105.0

# Check Point 106 network (alias)
auto eth0:106
iface eth0:106 inet static
name 106-Net
address 172.26.106.2
netmask 255.255.255.252
broadcast 172.26.106.3
network 172.26.106.0

---

### Post by lz1dsb on 2011-05-20
instructor@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.20.100.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
172.26.106.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
172.25.105.0    0.0.0.0         255.255.255.252 U         0 0          0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.10.1    0.0.0.0         UG        0 0          0 eth1

instructor@ubuntu:~$ arp -a
? (192.168.10.200) at 6c:f0:49:4f:47:8f [ether] on eth1
? (192.168.10.2) at 00:1d:73:b3:2c:1e [ether] on eth1
? (192.168.10.1) at 00:06:4f:66:0f:b1 [ether] on eth1

From a networking perspective it looks fine. What I'm worried about though is for example the look of your routing table. I'm not sure whether the system is getting the commands correctly. As you can see on your routing table the only outbound interface for the networks: 172.20.100.0/30 172.26.106.0/30, 172.25.105.0/32 is eth0. The alias interfaces eth0:105 and eth0:106 aren't mentioned. So I'm not sure if this is correct, I have to research a bit. It just doesn't look right though...
Also your arp table is showing MAC addresses learned from eth1. When you try ping from the Ubuntu server to the hosts in networks: 172.20.100.0/30 172.26.106.0/30, 172.25.105.0/32 do you get additional entries in your ARP table?
And also vice versa, do you get any entries on the FWs when you try to ping the Ubuntu server?


Cheers,
Boyan

---

### Post by lz1dsb on 2011-05-24
I just stumble upon this thread:
[http://ubuntuforums.org/showthread.php?t=1762413](http://ubuntuforums.org/showthread.php?t=1762413)

One of the guys mentions that you need to uncomment the following line:
net.ipv4.ip_forward=1
from the file /etc/sysctl.conf. 
I think that this is maybe what you need in your case. Could you check it out...


Cheers,
Boyan

---

