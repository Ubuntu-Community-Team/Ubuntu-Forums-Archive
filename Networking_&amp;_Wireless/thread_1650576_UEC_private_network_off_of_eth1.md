---
title: "UEC private network off of eth1"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by wcorey on 2010-12-21
I have this problem I have been wrestling with for some time. The roots of this problem have to do with Ubuntu Enterprise Cloud configuration.  To fast forward, On my desktop machine U10.10 Desktop I added the Eucalyptus 2.x packages so this machine will be my normal desktop (no Windows here) as well as cloud/cluster/storage controller for my cloud. Originally, 9.04 days, I had it installed on this machine and a second machine the node controller. Both machines were plugged into my router 192.168.0.0 and fed addresses from it. What I noticed was after a time the public (elastic IP) address of running instances would simply go away. I think the problem was how it renewed its lease...perhaps. So looking at the Eucalyptus diagrams that configuraton ONLY worked with System mode, not ManagedNoVlan as it was configured by Ubuntu on install.

So now I have my Desktop U10.10 Desktop on a machine with two NICs

eth0 - 192.168.0.0 (router is dhcp)
eth1 - 192.168.1.0 (dhcp3 is supposed to be dhcp for it)

eth1 goes to a Netgear 5 port switch. I have my old node controller and old cluster controller plugged into it and they, too, should be assigned addresses in the 192.168.1.x subnet.
<code>
walt@cor720:~$ sudo lspci|grep Ethernet
02:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
</code>

<code>walt@cor720:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:4f:b4:e2:b5  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4fff:feb4:e2b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21821968 (21.8 MB)  TX bytes:2321573 (2.3 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:10:18:09:af:40  
          inet6 addr: fe80::210:18ff:fe09:af40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7385 (7.3 KB)  TX bytes:771999 (771.9 KB)
          Interrupt:18 

eth1:avahi Link encap:Ethernet  HWaddr 00:10:18:09:af:40  
          inet addr:169.254.5.88  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 
</code>

<code>
walt@cor720:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
#auto eth1
iface eth1 inet manual
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.0 
</code>

walt@cor720:~$ cat /etc/default/dhcp3-server 
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
<code>
walt@cor720:~$ cat /etc/dhcp3/dhcpd.conf 
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#


option domain-name "corey.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
}
</code>

I am at a loss. eth0, as you can see, seems fine. eth1 does not even have the static address assigned in interfaces. eth1.avahi (what is that anyway?) has an address but it is pointing somewhere else entirely. 

I would greatly appreciate it if someone would point out where my mistake is or ask for info I haven't provided here.

Thanks,
Walt

---

### Post by h4lfl1ng on 2011-05-27
Why hasn't anyone replied to this yet? I'm having a similar problem, but I have a bridge setup on the node, which bridges eth0. On the cluster/cloud controller, I have eth0 (university internet) and eth1(switch with 8 pc's, only working on one first). I don't have access to the computer now, so I can't post any of the configs or results from commands, but what would i need to do to get the server to ping the node controller box? I did not do anything to the dhcp daemon, would that be my problem, do I have to setup a DHCP server..?  I'm running Ubuntu Server 11.04 though..

---

### Post by wcorey on 2011-05-27
WOW, thank you for yelling at them. Sometimes community software support sucks. Here's what I did that has everything working just fine.

What I called my desktop, is still my desktop NOT the everything but node controller I wanted to make it. So I parted with another $1,000 to get another Dell to be the everything but node controller. It works fine except I have a 6 GB 2.6Ghz box just running the clc, cc, sc, walrus etc. Seems like a waste to me. Come to find out that diagram that shows system/static mode running in a 2 machine config can actually run in a 3 machine config..

I think my problem was, as I speculated, 2 DHCP daemons were thinking they owned that ip address. I BELIEVE it would have worked had I changed the vnet_mode to system as that would allow the instances to ask the router to provide an IP and the cc would have stayed out of its way. 

One thing that I am exceptionally weak on is networking and iptables manipulation.  

I, too, had a bridge on my node controller. They were on a separate subnet to avoid the issue of two 'owning' dhcp3 servers. As I said, that works splendidly. I had tried, at work, to set up a single source system mode euca on a dedicated machine but in that mode you don't have any metadata service (I don't understand why but you don't). I nexted tried a 2 node setup as I initially described in this issue where the everything but is a desktop and the other machine is strictly node controller. Then I had Walrus issues.  Unfortunately the internals people I know at Euca were in Budapest so nobody on that forum answered either. I then tried OpenStack which is even more fragile than euca. 

If you have issues with UEC your best bet is to go to the Eucalyptus community forums. Ubuntu has thrown Eucalyptus under the bus anyway. That's too bad too as Euca is further down the maturation curve than OpenStack. But, starting in October, UEC will be OpenStack.

Walt

---

