---
title: "Me vs. the Gateway of Doom..."
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by kup3rt1n0 on 2006-07-10
First of all here is my disclaimer:

Although not new to linux, it HAS been a little while (I'm so happy to have a linux box again!) and this IS my first time with Ubuntu. That being said...

Okay, here's the problem. I have a small network of 4 machines. I have a cable modem connected to a Linksys WRT54G as my router. I have 3 machines wireless (2 Windows, 1 Mac) and the Ubuntu box is hard-wired. My network is 192.168.1.0/24. My router acts as a DHCP server with an IP pool of .100-.125. I have a static IP on the Ubuntu box of 192.168.1.2. All the machines connect fine except the Ubuntu box. I can ping the other machines on my network, but I can't ping the gateway. Every time I try to ping the gateway from the Ubuntu box, I get a destination host unreachable. Every other machine can ping the gateway fine. This seems a bit odd because the Ubuntu box has to go THROUGH the gateway in order to ping the other machines. Needless to say, I don't have Internet connectivity either. Here is the output of route -n:

Destination     Gateway     Genmask    Flags Metric Ref Use Iface
192.168.1.0     0.0.0.0     255.255.255.0  U     0    0   0 eth1
0.0.0.0         192.168.0.1 0.0.0.0       UG     0    0   0 eth1

I have 2 ethernet interfaces, but eth0 is disabled. Here is the contents of /etc/network/interfaces

#The loopback network interface
auto lo
iface lo auto loopback

#The primary network interface
auto eth1
iface eth1 inet static
     address 192.168.1.2
     netmask 255.255.255.0
     network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.1
     dns-nameservers 192.168.1.1
     dns-search hawaii.rr.com

This is probably something simple I have just overlokked, but any help or ideas would be appreciated.

FYI: This is the basic LAMP install, so I don't have the GUI.

---

