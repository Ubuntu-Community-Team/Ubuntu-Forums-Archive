---
title: "PC Router between wireless and Ethernet interface"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by BoonPing on 2010-09-02
Hi,

I tried to setup a connection as below but face some problem (probably  route table setting incorrect). Hope if anyone could shed the light...

Basically, I have a PC1 (.1) and PC2 (.130) connected via a PC router.  PC router has 2 interfaces: wireless (.2) and ethernet (.129). PC1  connects to PC router via LAN cable/wireless interface, while PC2  connects to PC router via cable. This settings try to simulate 1  wireless connection along the path (and because PC2 is too old to  support wireless interface, we need a PC router). These interfaces are  all under same 172.16.130.x subnet.

[PC1](.1)--ethernet--[wireless AP]--wireless--(.2)[PC router](.129)--ethernet--[dummy switch]--ethernet-- (.130)[PC2]


I tried to check the settings at PC router by PING.
The problem is 
  [LEFT][SIZE=2](a)[COLOR=black][FONT=Arial]PING success from .1 to .129, [/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](b)[COLOR=black][FONT=Arial]PING fail from .129 to .1.[/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](c)[COLOR=black][FONT=Arial]PING success from .130 to .2[/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](d)[COLOR=black][FONT=Arial]PING fail from .2 to .130.      [/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](e)[COLOR=black][FONT=Arial]PING fail from .1 to .130 (ICMP request from .1 reach .2 but does not forward to .129)[/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](f)[COLOR=black][FONT=Arial]PING fail from .130 to .1[/FONT][/COLOR][COLOR=black][FONT=Arial]   ([/FONT][/COLOR][COLOR=black][FONT=Arial]ICMP request from .130 reach .129 but does not forward to .2)[/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](g)[COLOR=black][FONT=Arial]PING success between adjacent interface ([/FONT][/COLOR][COLOR=black][FONT=Arial]eg[/FONT][/COLOR][COLOR=black][FONT=Arial]. .1 to .2 and vice versa, .129 to .130 and vice versa).[/FONT][/COLOR][/SIZE][/LEFT]
  [LEFT][SIZE=2](h)[COLOR=black][FONT=Arial]PING fail between .129<>.2 using non loopback fail (expected since no [/FONT][/COLOR][COLOR=black][FONT=Arial]conn[/FONT][/COLOR][COLOR=black][FONT=Arial] btw 2 interface).[/FONT][/COLOR][/SIZE][/LEFT]
  

My question is why PING A -> B success, but PING B->A fail??


--------------------------------------------
Below are the settings of Ubuntu 9.04 at PC Router
--------------------------------------------

root@atdg-desktop:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.130.128  0.0.0.0         255.255.255.128 U     1      0        0 eth0
172.16.130.0    0.0.0.0         255.255.255.0   U     2      0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.130.2    0.0.0.0         UG    0      0        0 ra0
0.0.0.0         172.16.130.129  0.0.0.0         UG    0      0        0 eth0

-----------------------

root@atdg-desktop:~# sysctl -a | grep forward
error: "Invalid argument" reading key "fs.binfmt_misc.register"
error: permission denied on key 'net.ipv4.route.flush'
net.ipv4.conf.all.forwarding = 1
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.lo.forwarding = 1
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.eth0.forwarding = 1
net.ipv4.conf.eth0.mc_forwarding = 0
net.ipv4.conf.eth1.forwarding = 1
net.ipv4.conf.eth1.mc_forwarding = 0
net.ipv4.conf.ra0.forwarding = 1
net.ipv4.conf.ra0.mc_forwarding = 0
net.ipv4.conf.pan0.forwarding = 1
net.ipv4.conf.pan0.mc_forwarding = 0
net.ipv4.ip_forward = 1
net.ipv6.conf.all.forwarding = 0
net.ipv6.conf.default.forwarding = 0
net.ipv6.conf.lo.forwarding = 0
error: permission denied on key 'net.ipv6.route.flush'
net.ipv6.conf.eth0.forwarding = 0
net.ipv6.conf.eth1.forwarding = 0
net.ipv6.conf.ra0.forwarding = 0
net.ipv6.conf.pan0.forwarding = 0

----------------------------------

root@atdg-desktop:~# cat /proc/sys/net/ipv4/ip_forward 
1

----------------------------------

root@atdg-desktop:~# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


----------------------------------

root@atdg-desktop:~# arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
172.16.130.130           ether   [CorrectMAC]   CM                    ra0
172.16.130.130           ether   [CorrectMAC]   C                     eth0
172.16.130.1           ether   [CorrectMAC]   CM                    ra0
172.16.130.1           ether   [CorrectMAC]   C                     eth0

---

### Post by BkkBonanza on 2010-09-02
I didn't figure out all your routing and details there but it looks to me like you have overlapping networks. 

172.16.130.0/24
172.16.130.128/25

Which likely gives you different routes depending on direction.
Also you have two default gateways set. Not sure how that plays out but if it round-robins on them then perhaps one path isn't correct. Pinging multiple times with different results could indicate that.

Using traceroute instead of ping could show you more.

---

### Post by BoonPing on 2010-09-02
> 172.16.130.0/24
172.16.130.128/25

Which likely gives you different routes depending on direction.

Ya. You're right.
I have set net.ipv4.conf.all.forwarding = 1  in PC Router and hoping both ra0 and eth0 interface would forward packets between each other.


> Also you have two default gateways set. 
This is the part that I'm not quite sure it's correct or even if it's effective?!

I tried traceroute but it does not give in-sight of how packet is routed in PC router since traceroute assumed it's single hop.

To make the question simple.......
Why trigger the below command in PC router fail?  
> ping 172.16.130.130 -I ra0  

:cry:.  Ain't PC router should route/forward it such as   .2 -> .129 -> .130  for echo request, then .130 -> .129 -> .2 for echo reply?

---

### Post by BoonPing on 2010-09-02
Hmm... I resolved this problem by 
a)  changing 2 interfaces for PC router into different subnet.  Wireless subnet 130.x, and Ethernet subnet  140.x

[PC1](.130.1)--ethernet--[wireless AP]--wireless--(.130.2)[PC router](140.1)--ethernet--[dummy switch]--ethernet-- (140.2)[PC2]

b) at PC1 , because vlan is enabled here, I have added route towards 140.x

[COLOR=black][FONT=Arial]sudo[/FONT][/COLOR][COLOR=black][FONT=Arial] route add –net 172.16.140.0 dev vlan130 [/FONT][/COLOR][COLOR=black][FONT=Arial]netmask[/FONT][/COLOR][COLOR=black][FONT=Arial] 255.255.255.0[/FONT][/COLOR]


Just making note for future reader. I guess PC forwarder does not work for same subnet, question remain unanswered...

---

