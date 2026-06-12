---
title: "ubuntu and win wont ping but address gets assigned"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by koszta on 2010-12-04
Hey I am really confused about this I have two machines 
1. Ubuntu (static IP 192.168.1.1, running dhcp server)
2. Windows 7 (dhcp assigned IP based on mac - >192.168.1.2) 

Now when I fire up both machines, Linux assigns IP to win BUT they dont ping. :( From ifconfig I know:

eth2      Link encap:Ethernet  HWaddr 00:1b:21:7b:2d:68  
          inet addr:192.168.1.1  Bcast:192.168.1.3  Mask:255.255.255.252
          inet6 addr: fe80::21b:21ff:fe7b:2d68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14609 (14.6 KB)  TX bytes:3690 (3.6 KB)
          Memory:d8120000-d8140000 
route -n 
192.168.1.0     0.0.0.0         255.255.255.252 U     0      0        0 eth2
OUTSIDE IP   0.0.0.0         255.255.255.224 U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0        OUTSIDE IP   0.0.0.0         UG    100    0        0 eth0


From windows: 
destination                        mask                           gateway                              interface
0.0.0.0                                0.0.0.0                      192.168.1.1                       192.168.1.2

Now I get time exceeded icmp every time I try to ping both from linux OR windows... :( 

Pls I am really going crazy ... thnx

---

### Post by koszta on 2010-12-04
if I run :
sudo /etc/init.d/networking restart
I get:
...
SIOCADDRT: No such process
Failed to bring up eth2.
SIOCADDRT: No such process
Failed to bring up eth1.
   ...done.

here is my /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet static
external IP config, but this one works...

# DMZ network interface
auto eth2
iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.252
network 192.168.1.0
broadcast 192.168.1.3
gateway OUTSIDE IP

# LAN network interface
auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway OUTSIDE IP

---

### Post by koszta on 2010-12-04
Well it was my firewall :( what is wrong with it? 



#!/bin/bash
ipt=/sbin/iptables

#define interfaces
wan=eth0
dmz=eth2
lan=eth1
echo "setting up firewall variables"
echo "flushing tables"
#flush all tables
$ipt -F
echo "setting up default policies"
#set default policy
$ipt -P INPUT DROP
$ipt -P FORWARD DROP
$ipt -P OUTPUT ACCEPT
$ipt -t nat -P OUTPUT ACCEPT
$ipt -t nat -P PREROUTING ACCEPT
$ipt -t nat -P POSTROUTING ACCEPT
$ipt -t mangle -P PREROUTING ACCEPT
$ipt -t mangle -P POSTROUTING ACCEPT

#aceept all loopback traffic
$ipt -A INPUT -i lo -j ACCEPT

# accept ICMP
$ipt -A INPUT -p icmp --icmp-type echo-reply -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type echo-request -m limit --limit 5/s -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type destination-unreachable -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type time-exceeded -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type timestamp-request -m state --state NEW -j ACCEPT
$ipt -A INPUT -p icmp --icmp-type timestamp-reply -m state --state ESTABLISHED,RELATED -j ACCEPT

#enable masquarade 
$ipt -t nat -A POSTROUTING -o $dmz -j SNAT --to OUTSIDE IP
$ipt -t nat -A POSTROUTING -o $lan -j SNAT --to OUTSIDE IP
echo "setting up stateful firewall"
#stateful firewall basic rule
$ipt -A INPUT -i $wan -m state --state ESTABLISHED,RELATED -j ACCEPT
$ipt -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
echo "setting up interfaces policy"
#################################################
#          interfaces settings                  #
#################################################
echo "allowing services"
#################################################		
#	outside service allowance		#
#################################################
#ssh from Inet allowance 
$ipt -A INPUT -i $wan -p tcp --dport 22 --sport 1024:65535 -m state --state NEW -j ACCEPT
#allow mysql remote login
$ipt -A INPUT -i $wan -p tcp --dport 3306 --sport 1024:65535 -m state --state NEW -j ACCEPT

#################################################               
#       inside service allowance                #
#################################################
# allow LAN dhcp requests
$ipt  -I INPUT -i $lan -p udp --dport 68 --sport 67 -j ACCEPT
# allow DMZ dhcp requests
$ipt  -I INPUT -i $dmz -p udp --dport 68 --sport 67 -j ACCEPT

---

