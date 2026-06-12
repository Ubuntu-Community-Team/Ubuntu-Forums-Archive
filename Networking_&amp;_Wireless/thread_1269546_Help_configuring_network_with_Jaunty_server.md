---
title: "Help configuring network with Jaunty server"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by africantiger on 2009-09-18
Hi, I am trying to setup a home network with two computers, DSL Modem and a Dlink switch.
I have the following setup:

Jaunty server running dhcp server, 2 NICs (eth0 connected to modem, eth1 connected to switch)
Jaunty client connected to the switch
The dhcp server is running and working, I get the leased IP on my client computer

There is no internet connectivity, I cannot browse the web.

I have configured both eth0 and eth1 to be static (not sure if it should be like that):

Output from ifconfig is:

eth0      Link encap:Ethernet  HWaddr 00:11:25:07:c4:b4  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe07:c4b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2498726 (2.4 MB)  TX bytes:445441 (445.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:0a:cd:17:ad:33  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe17:ad33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38210 (38.2 KB)  TX bytes:17812 (17.8 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1266801 (1.2 MB)  TX bytes:1266801 (1.2 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:76.64.75.109  P-t-P:64.230.197.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2431526 (2.4 MB)  TX bytes:338699 (338.6 KB)

virbr0    Link encap:Ethernet  HWaddr de:58:34:90:e1:97  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::dc58:34ff:fe90:e197/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8749 (8.7 KB)

iptables -L shows the following:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Output from route is:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
bas2-ottawa10_l *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         *               0.0.0.0         U     0      0        0 ppp0


I have ip_forwarding enabled. I am not sure what I am missing. I suspect my firewall and gateway is not setup properly. Thanks for any and all help.


AfricanTiger

---

### Post by Iowan on 2009-09-18
The two interfaces should be in different subnets (unless they're bonded or is it bridged...) Eth0 should be in the same subnet as the modem. Dunno about the virbr0...
(My DSL modem acts like a router - with DHCP server, if desired - so I don't need to play with ppp, pppoe, or otherwise.)

---

