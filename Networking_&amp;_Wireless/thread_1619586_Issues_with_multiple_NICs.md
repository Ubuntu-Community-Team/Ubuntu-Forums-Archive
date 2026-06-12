---
title: "Issues with multiple NICs"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by richpowell on 2010-11-12
Hi all,
 
I'm having some strange issues when using multiple NICs in Ubuntu Server x64. I've used the same configuration with CentOS and Windows Server 2008 R2 and they both worked fine.
 
What's happening is that if either one of the interfaces exists on its own it works fine however as soon as I bring them up together I can no longer connect to the machine through it's public IP (eth0). For example, if I try and SSH into the machine when both interfaces are up, I can connect using the 10.1.10.11 address but not the 173.xxx.xxx.50 address. However, if I ifdown eth1, then suddenly I can both ping and SSH into the 173.xxx.xxx.50 address.
 
Here is my /etc/network/interfaces:
 
>  
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 173.xxx.xxx.50
netmask 255.255.255.248
gateway 173.xxx.xxx.54
auto eth1
iface eth1 inet static
address 10.1.10.11
netmask 255.255.255.0
 

 
And here is the output of route -n:
 
>  
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
173.xxx.xxx.48 0.0.0.0 255.255.255.248 U 0 0 0 eth0
10.1.10.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 173.xxx.xxx.54 0.0.0.0 UG 100 0 0 eth0
 

 
Thanks for the help!

---

### Post by richpowell on 2010-11-12
Well. What's even more strange is that if I rather use a single interface and assign the two ip addresses like this:
 
>  
# The primary network interface
auto eth0
iface eth0 inet static
address 173.160.184.50
netmask 255.255.255.248
gateway 173.160.184.54
broadcast 173.160.184.55
auto eth0:1
iface eth0:1 inet static
address 10.1.10.11
netmask 255.255.255.0
 

 
Everything works perfectly!
Oh well, I guess I'll just take out the second NIC. Looks like it's not necessary :)
 
It would, however, be interesting to understand why this doesn't work with two NICs.

---

