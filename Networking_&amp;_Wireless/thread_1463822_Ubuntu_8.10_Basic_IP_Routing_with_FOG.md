---
title: "Ubuntu 8.10 Basic IP Routing with FOG"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by rustyhann on 2010-04-27
I have a FOG imaging server setup on Ubuntu 8.10. It has two NICs, eth0 and eth1. I have setup the FOG system on eth1 which is connected to a 24 port switch. I have the eth0 NIC connected to an internet enabled switch and set to pick up DHCP. Here is what my /etc/network/interfaces looks like
 
auto eth0
iface eth0 inet dhcp
 
auto eth1
iface eth1 inet static
[INDENT]address 192.168.1.2
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
[/INDENT]All I want to do is allow the FOG clients to access the internet through the eth1 interface on the internet enabled switch so they can validate Windows. The FOG tutorial reccommends removing network-manager, and so I have done so, which rules out basic internet connection sharing. I need to be able to set up the routing manually. Any help would be appreciated.

---

### Post by Iowan on 2010-04-27
Perhaps you've already seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page?

---

### Post by rustyhann on 2010-04-30
After reading the manpage a few hundred times, and a few CentOS articles, and the link posted above, I think I have it.  In the example given in the Ubuntu 9.10 tutorial, a 4th rule has to be stated.  This is what I think it might have to be:

```
sudo iptables -A FORWARD -i eth1 -o eth0 -s 10.164.144.0/20 -m conntrack --cstate NEW -j Accept
```

This is to allow two way traffic in and out of the network.

In my scenario, I have a vlan which is connected to the internet (10.164.144.0/20).  I have a private lan that I run FOG on (192.168.1.0/24).  With both of the forward rules applied, clients on the 192 network will be able to send and receive connections from the 10 network and the internet.  Am I correct in my thinkinbg?

---

