---
title: "ICS in ppoe internet connection type"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by speedy18us on 2009-11-14
i have 2 computers: one of it as a server and ICS with Ubuntu server 9.10 and another one with winxp.
on the first computer the internet is working fine (throught ppoeconf utility) , the second enthernet card has 192.168.0.1, but i can't make ICS.

1.i've used the following commands for the enthernet card with the internet (eth1):
sudo pppoeconf (all the settings were good)

2.i've used the following commands for the enthernet card with the ICS (eth0):


**Code:**

ifconfig eth0 down
ifconfig eth0 192.168.1.1 netmask 255.255.255.0 up

iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE
iptables --append FORWARD --in-interface eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward


The last command gives me this error:

-bash: /proc/sys/net/ipv4/ip: No such file or directory


3.listing the network cards gives me this:


**Cod:**

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3840 (3.8 KB)  TX bytes:3840 (3.8 KB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:79.xxx.xxx.xxx  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:27389 (27.3 KB)  TX bytes:27171 (27.1 KB)


eth0      Link encap:Ethernet  HWaddr 00:0e:e8:e6:4d:69
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:e8ff:fee6:4d69/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148570 (148.5 KB)  TX bytes:115837 (115.8 KB)
          Interrupt:9 Base address:0x7000

eth1      Link encap:Ethernet  HWaddr 00:0e:e8:e6:4b:f7
          inet addr:10.10.6.174  Bcast:10.10.7.254  Mask:255.255.252.0
          inet6 addr: fe80::20e:e8ff:fee6:4bf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:396943 (396.9 KB)  TX bytes:368671 (368.6 KB)
          Interrupt:7 Base address:0x7400

4.with the command sudo iptables -L -t nat i have the followings:

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
MASQUERADE  all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

5.restarting network service (sudo /etc/init.d/networking restart) gives me this (and eth0 down):


**Code:**

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 2342
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:e8:e6:4b:f7
Sending on   LPF/eth1/00:0e:e8:e6:4b:f7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.10.0.2 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
Don't seem to be have all the variables for eth0/inet.
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0e:e8:e6:4b:f7
Sending on   LPF/eth1/00:0e:e8:e6:4b:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.10.6.174 from 10.10.0.2
DHCPREQUEST of 10.10.6.174 on eth1 to 255.255.255.255 port 67
DHCPACK of 10.10.6.174 from 10.10.0.2
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 10.10.6.174 -- renewal in 38841 seconds.

6.the file /etc/network/interfaces contains :


**Code:**

# The loopback network interface
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet static
adress 192.168.0.1
gateway 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

iface eth1 inet dhcp
auto eth1


7. in /etc/sysctl.conf este decomentat 

net.ipv4.conf.default.forwarding=1

Question: what am i doing wrong?

---

### Post by speedy18us on 2011-11-24
Finally, in November 25, 2009 I was being able to make ICS. I wrote a post on my blog [http://ubuntu-for-humans.blogspot.com/2009/11/configure-internet-connection-sharing.html](http://ubuntu-for-humans.blogspot.com/2009/11/configure-internet-connection-sharing.html)

---

