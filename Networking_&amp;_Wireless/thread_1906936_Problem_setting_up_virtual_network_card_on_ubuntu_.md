---
title: "Problem setting up virtual network card on ubuntu for use with Clonezilla"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by Mikken on 2012-01-10
Hi
I'm trying to set up Clonezilla on a fresh Ubuntu install, following this tutorial:
[http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/](http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/)

It mostly works out ok, but i have some problems setting up the virtual network card. This is my interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.113
netmask 255.255.255.0
broadcast 0.0.0.0
gateway 192.168.3.1

auto eth0:0
iface eth0:0 inet static
address 192.168.99.113
netmask 255.255.255.0


I restarted network using sudo /etc/init.d/networking restart, but when i run ifconfig the eth0:0 does not show up. 

What do I miss here?

---

### Post by Mikken on 2012-01-11
This is my ifconfig output:
eth0      Link encap:Ethernet  HWaddr bc:30:5b:ac:fd:9b  
          inet addr:192.168.3.113  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::be30:5bff:feac:fd9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7568701 (7.5 MB)  TX bytes:637766 (637.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

This is the output when i restart network:
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          RTNETLINK answers: File exists
Failed to bring up eth0.
Ignoring unknown interface eth0:0=eth0:0.

---

### Post by Mikken on 2012-01-12
...just an update of my problem, in case someone got the same woes as me:

Changing my eth0:0 ip to 172.16.1.1 worked; seems my NIC doesn't support multiple IP addresses.

Now, if anyone knows how to solve *that*, I'd be grateful!

---

