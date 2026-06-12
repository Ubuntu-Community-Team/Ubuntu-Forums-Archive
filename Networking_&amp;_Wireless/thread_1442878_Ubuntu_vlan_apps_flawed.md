---
title: "Ubuntu vlan apps flawed?"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by dvlabguy on 2010-03-30
I have one of the top three telecom giants (not named Cisco or Juniper) tell me Ubuntu is flawed and will not work on thier routers with vlans for dhcp. They said to just use Windows 2008 Server.
 
I've attempted to solve this without any responses in this forum, so this may be true what they are saying, but I'd like to challange the Ubuntu forum guru's to prove them wrong.
 
Network topology below...
 
DHCP Client -- L2 Switch -- L3 router -- Ubuntu DHCP Server.
 
The client on the L2 switch is setup to request a DHCP address via Vlans 500-999, ea Vlan has a range of 12 IPs.
 
eth0  (mgt ip)    
Link encap:Ethernet  HWaddr 00:19:b9:30:60:03
          inet addr:10.15.12.11  Bcast:10.15.12.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe30:6003/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5363851 (5.3 MB)  TX bytes:199057 (199.0 KB)
          Interrupt:16
 
eth3  (connected to router port)
Link encap:Ethernet  HWaddr 00:13:46:72:41:c6
          inet addr:10.77.50.1  Bcast:10.77.50.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe72:41c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2178 (2.1 KB)  TX bytes:33517 (33.5 KB)
          Interrupt:18
 
eth3.500 (sub-interface for vlans with dhcp ranges)
Link encap:Ethernet  HWaddr 00:13:46:72:41:c6
          inet addr:10.115.50.1  Bcast:10.115.50.15  Mask:255.255.255.240
          inet6 addr: fe80::213:46ff:fe72:41c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:22311 (22.3 KB).
 
----
 
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# cat /etc/dhcp3/dhcpd.conf
  subnet 10.115.50.0 netmask 255.255.255.240 {
  option subnet-mask 255.255.255.240;
  option domain-name-servers 10.15.12.100;
  option domain-name aaa.bbb.com;
  option routers 10.115.50.1;
  option broadcast-address 10.115.50.15;
  default-lease-time 600;
  max-lease-time 7200;
  option ip-forwarding on;
  range dynamic-bootp 10.115.50.2 10.115.50.14; }
 
----
 
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 10.15.12.11
netmask 255.255.255.0
network 10.15.12.0
broadcast 10.15.12.255
gateway 10.15.12.1
ifup /sbin/route add -net 10.15.12.0 netmask 255.255.255.0 gw 10.15.12.1 dev eth0
# Secondary interface via Router 10.77.50.2 for DHCP
auto eth3
iface eth3 inet static
address 10.77.50.1
netmask 255.255.255.0
network 10.77.50.0
broadcast 10.77.50.255
gateway 10.77.50.1
ifup /sbin/route add -net 10.77.50.0 netmask 255.255.255.0 gw 10.77.50.1 dev eth3
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth3.500 (for vlan500)
iface eth3.500 inet static
address 10.115.50.1
netmask 255.255.255.240
network 10.115.50.0
broadcast 10.115.50.15
mtu 1500
vlan_raw_device eth3
!
!
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.15.12.11     0.0.0.0         255.255.255.255 UH        0 0          0 eth0
10.115.50.0     0.0.0.0         255.255.255.240 U         0 0          0 eth3.500
10.15.12.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.77.50.0      0.0.0.0         255.255.255.0   U         0 0          0 eth3
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.15.12.1      0.0.0.0         UG        0 0          0 eth0
0.0.0.0         10.77.50.1      0.0.0.0         UG        0 0          0 eth3
0.0.0.0         10.15.12.1      0.0.0.0         UG        0 0          0 eth0
!
!
[EMAIL="root@ubuntu:/etc"]root@ubuntu:/etc[/EMAIL]# cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
8021q
!
!
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# iptables -L -v
Chain INPUT (policy ACCEPT 7924 packets, 869K bytes)
 pkts bytes target     prot opt in     out     source               destination 
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
Chain OUTPUT (policy ACCEPT 4563 packets, 643K bytes)
 pkts bytes target     prot opt in     out     source               destination
!
!
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# ping 10.77.50.2 (Router ip int)
PING 10.77.50.2 (10.77.50.2) 56(84) bytes of data.
64 bytes from 10.77.50.2: icmp_seq=1 ttl=64 time=3.74 ms
64 bytes from 10.77.50.2: icmp_seq=2 ttl=64 time=0.735 ms

---

### Post by terazen on 2010-03-30
Not to get off topic, but I'm curious why you are using trunking on your dhcp server.  Is it a requirement for something?

---

### Post by dvlabguy on 2010-03-30
terazen,
 
We wanted to keep it in Trunk mode to keep the vlan/8021q tag.
 
For example, our client will request a dhcp address (via bootp) on vlan 500 (ranges 10.115.50.2-10.115.50.14 via GW 10.115.50.1.), which will traverse the L2 vlan500 interface, then route to the DHCP server via L3 and should receive the ICMP request.
 
I can include a wireshark cap file if needed?

---

### Post by terazen on 2010-03-30
It doesn't sound like you need trunking.  The dhcp server should know which range of ip addresses to use based on the request it receives from the router that forwarded it.

I've never set up trunking on a linux box, but I'd hate for you to setup a windows box for just dhcp.

---

### Post by dvlabguy on 2010-03-30
terazen,
 
Are you suggesting just using ETH3 and not ETH3.500 and forget about the 8021q?

---

### Post by terazen on 2010-03-30
That's how I have always done it.  I can't speak for folks I've never met but that's how I assume 99.99% of dhcp servers are setup.

---

### Post by dvlabguy on 2010-03-30
So should I get rid of ETH3.500 and just use ETH3?
 
Also, see attached jpeg of the wireshark capture.

---

### Post by terazen on 2010-03-30
> So should I get rid of ETH3.500 and just use ETH3?

Yes.  You could use eth0 or eth3.

For instance, I have 2 dhcp servers each connected to different routers at different locations and they each have 1 ip address.  They mirror each other and both serve 20+ vlans and about 800 devices.  I use cisco routers so I just configure "ip helper-address a.b.c.d" on each vlan dhcp is setup for.  Not sure about what kind of router you use, but I'm sure there is a pdf somewhere to tell you where you configure the dhcp server ip address.

---

### Post by dvlabguy on 2010-03-31
terazen,
 
Can you share your router/dhcp server configs?
 
I'm actually usng an ALU 7750 with the following config that has a helper address as well.
 
ies 500 customer 1 create
    interface "i500" create
        address 10.115.50.1/28
        dhcp
            server 10.77.50.1
            trusted
            gi-address 10.115.50.1
            no shutdown
 
i'd be will to put it on a secure/public ip if you're really interested? :D

---

### Post by terazen on 2010-03-31
I've never used Alcatel, but if your /var/log/syslog file shows dhcp requests then you just need to setup the dhcp server config.

[http://www.bind9.net/manuals-dhcp](http://www.bind9.net/manuals-dhcp)

---

