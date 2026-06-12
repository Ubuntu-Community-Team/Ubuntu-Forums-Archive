---
title: "need help with bonding vlan's"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by creigan192 on 2009-06-03
So here is what I'm trying to do. I have a server that has two gig Ethernet ports (eth0-eth1). These ports need to be in trunks and not bound together. The trunk's will carry four vlan's each  so eth0 will carry vlan 2-5 and eth1 will carry vlan 2-5. here is my question I need to bond the vlan's together in the scene that vlan 2 would be bond0 vlan 3 would be bon1 and so on. how do I go about doing this. 
The server is connected to two different switches for redundancy.
There is a network drawing attached to this post.

---

### Post by abequer on 2009-06-03
Hi
 
I had the same configuration need and I just solved it. With this configuration you can have high-availability of several VLANs with just two cables (one for each switch). 
 
What I did is to have one single bonding including the two phisical interfaces eth0 and eth1. Over the bond0 I configured two VLAN interfaces, of course you could have as many as you want.
 
To configure the bond0 what I did is placing the following code in the file /etc/network/interfaces:
 
[FONT=Courier New][SIZE=1][COLOR=dimgray]auto bond0 #Create the interface[/COLOR][/SIZE][/FONT]
[SIZE=1][FONT=Courier New][COLOR=dimgray]iface bond0 inet manual #No IP will be assigned[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]post-up ifenslave bond0 eth0 eth1 #on start Asociate eth0 and eth1[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]post-up vconfig add bond0 216 #on start, create vlan 216[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]post-up vconfig add bond0 214 #on start create vlan 214[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]pre-down vconfig rem bond0.214 #on stop, delete valn 214[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]pre-down vconfig rem bond0.216 #on stop, delete vlan 216 [/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]pre-down ifenslave -d bond0 eth0 eth1 #on stop, deasociate eth0 and eth1[/COLOR][/FONT][/SIZE]
 
With the previous steps you shuld have created the interfases that you need. Then in the same file I placed the definition of the VLAN interfaces IP addresses as usual
 
[FONT=Courier New][SIZE=1][COLOR=dimgray]auto bond0.216[/COLOR][/SIZE][/FONT]
[SIZE=1][FONT=Courier New][COLOR=dimgray]iface bond0.216 inet static[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]address 10.216.47.23[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]netmask 255.255.255.0[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]broadcast 10.216.47.255[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]gateway 10.216.47.6[/COLOR][/FONT][/SIZE]
[FONT=Courier New][SIZE=1][COLOR=dimgray]auto bond0.214[/COLOR][/SIZE][/FONT]
[SIZE=1][FONT=Courier New][COLOR=dimgray]iface bond0.214 inet static[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]address 10.216.45.34[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]netmask 255.255.255.0[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]broadcast 10.216.45.255[/COLOR][/FONT][/SIZE]
 
One other think, in /etc/modprobe.d/aliases I configured an Active-Passive policy for the bonding with the following lines:
 
 
[SIZE=1][FONT=Courier New][COLOR=dimgray]# Alias for bonding[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]alias bond0 bonding[/COLOR][/FONT][/SIZE]
[SIZE=1][FONT=Courier New][COLOR=dimgray]options bonding mode=1 miimon=100[/COLOR][/FONT][/SIZE]
 
 

[SIZE=2][COLOR=black]I hope this will help you. [/COLOR][/SIZE]
 
[FONT=Courier New][SIZE=1][COLOR=dimgray][FONT=Verdana][SIZE=2][COLOR=black]Regards!!![/COLOR][/SIZE][/FONT]
[/COLOR][/SIZE][/FONT]

---

