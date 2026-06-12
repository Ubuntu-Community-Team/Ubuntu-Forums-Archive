---
title: "Ubuntu 8.04 LTS gateway problems"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by c0mputerking on 2011-09-05
**                     8.04 LTS Default gateway problems                 **
[INDENT]                             When my machine boots my route command looks like below, and I can ping my gateway, but not the Internet.  
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.xxx.xxx.128 *               255.255.255.224 U     0      0        0 eth0
 
The only way i can get to the Internet is to manually run route add  default gw xxx.xxx.xxx.129 after which my route looks like this.
 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
204.244.122.128 *               255.255.255.224 U     0      0        0 eth0
default         204.244.122.129 0.0.0.0         UG    0      0        0 eth0
 
However in my /etc/network/interfaces I clearly have my gateway defined as xxx.xxx.xxx.129
 
# The loopback network interface
auto lo eth0
iface lo inet loopback
 
# The primary network interface
iface eth0 inet static
        address xxx.xxx.xxx.132
        netmask 255.255.255.224
        broadcast xxx.xxx.xxx.159
        network xxx.xxx.xxx.128
        gateway xxx.xxx.xxx.129
#       metric 0
#       up route add default gw 204.244.122.129
 
Also when i do a /etc/init.d/networking restart i get some 
[[COLOR=blue][FONT=inherit ! important][FONT=inherit ! important]errors[/FONT][/FONT][/COLOR]]("http://www.linuxforums.org/forum/#") but Internet access continues to work see below. 
 
* Reconfiguring network interfaces...                                          Moving from lan,netstart to if-pre-up,eth0,lan
SIOCADDRT: No such process
Failed to bring up eth0.
 
Please help as this machine is located in a datacenter so access is limited                         [/INDENT]

---

