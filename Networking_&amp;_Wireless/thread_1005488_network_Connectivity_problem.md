---
title: "network Connectivity problem"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by eAbedul on 2008-12-08
Hi all, I'm new at Ubuntu and I'm having weird problem with the net. Iternet is fine and my Ubuntu ca be pinged from a windows laptop I have. But I am unable to reach the laptop from Ubuntu (it has no fw) and I can't connect to services such as ftp from my laptop. ftp works to the local IP but not for localhost.

if I traceroute to the windows I don't even get to the router, so I added a static route and now I reach the router but that's it. What makes me drive nuts is that it replys well to ICMP from the windows.

I had not this problem with windows, so I wonder if theres a firewall/filter or something I'm missing. 

That's my iptables output:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

thank you for your help.

---

### Post by Iowan on 2008-12-08
> **eAbedul said:**
> ftp works to the local IP but not for localhost.
The laptop can connect Ubuntu by IP address but not by **localhost**? That would be normal - localhost for the laptop would be the laptop.  ...or are you talking about localhost from Ubuntu?

---

### Post by eAbedul on 2008-12-09
Sorry I was not too clear. In Ubuntu ftp localhost don't work and ftp IP (The IP on eth0) works. 
In Ubuntu, ping to XP_Box -> no reply
In XP_Box, ping to Ubuntu_Box > Reply

I said the ftp as an example. I tried samba and telnet, but no connectivity. I think there is something that don't allow Ubuntu to reach the XP, wich is in the same LAN.

---

### Post by awreneau on 2008-12-09
Can you ping the gateway?
Can you nslookup some domain name?

---

### Post by superprash2003 on 2008-12-09
do you run any 3rd party firewall in xp?

---

### Post by eAbedul on 2008-12-09
No firewalls, and I can ping the gw.

I have a partition in the the buntu box with windows. I boot it and ping works. I boot Ubuntu and no ping. 

My routes:
192.168.1.0     0.0.0.0         255.255.255.0   U      0 0     0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG     0 0     0 eth0

And look at this:

root@tebas:/etc# tracepath 192.168.1.34 
1:  home.local (192.168.1.46)              0.090ms pmtu 1500
 1:  no reply
^C
root@home:/etc# tracepath 192.168.1.1
 1:  home.local (192.168.1.46)             0.087ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)             0.760ms reached
 1:  192.168.1.1 (192.168.1.1)             0.747ms reached
     Resume: pmtu 1500 hops 1 back 155 
root@home:/etc#

---

### Post by superprash2003 on 2008-12-10
are you pinging via hostname or ip?

---

### Post by Pixtu on 2008-12-10
If I follow this correctly, XP to Linux works but Linux to XP doesn't.

I have the same problem but I'm taking this to be a problem with the Windows system rather than the Linux system.

In my case:
I can ping from XP to other XP and to Linux
I can ping from Linux to one XP but not the other
I also have a problem when I try and browse the network from the XP system
I can browse the network and see all XP systems from Linux

So I think that there must be some form of config error on the XP system.

---

