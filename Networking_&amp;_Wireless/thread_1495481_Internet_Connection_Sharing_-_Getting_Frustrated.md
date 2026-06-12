---
title: "Internet Connection Sharing - Getting Frustrated"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by luceerose on 2010-05-28
Trying to share my internet connection with other computers on my LAN. I've tried doing this with Debian, Ubuntu & Fedora so far...
My Intended Setup is as follows;
[ATTACH]158510[/ATTACH]

The Problem: So far I've not been able to get an internet connection from any computer connected to the HUB.
I currenty have Fedora 13 on PC1 but have also tried with both Ubuntu 10.04 & Debian Lenny.
I am open to using any Linux based distro on PC1 as long it has a Gnome Desktop.
eth0 on PC1 can be Static or Dhcp, but I would prefer to set Static IPs on eth1 & all of the Client PCs

To the best of my knowledge I have enabled ipv4 forwarding in sysctl.conf (& some other changes);
```
net.ipv4.ip_forward = 1
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.accept_source_route = 0
kernel.sysrq = 0
kernel.core_uses_pid = 1
net.core.rmem_max = 16777216 
net.core.wmem_max = 16777216 
net.ipv4.tcp_rmem = 16777216 
net.ipv4.tcp_wmem = 16777216 
net.ipv4.tcp_no_metrics_save = 1 
net.ipv4.tcp_moderate_rcvbuf = 1 
net.core.netdev_max_backlog = 2500 
net.ipv4.tcp_timestamps = 0 
net.ipv4.tcp_sack = 0 
net.ipv4.tcp_window_scaling = 1
```

[CONTINUED in POST #2]...

---

### Post by luceerose on 2010-05-28
PC1's ip configuration ( i've placed XXX over the 3rd section of all my addresses);

[ATTACH]158513[/ATTACH] [ATTACH]158514[/ATTACH]

All changes I made to the Firewall (all other Firewall settings are still at default, no custom rules added yet);

[ATTACH]158515[/ATTACH] [ATTACH]158516[/ATTACH] [ATTACH]158517[/ATTACH]

Router is set up to assign dhcp from 192.168.xxx.100 & 192.168.xxx.200

At the moment I have only 1 PC attached to the HUB. It's Ubuntu 10.04 (PC2)
It's details are;
ip 192.168.xxx.103
netmask255.255.255.0
gateway 192.168.xxx.101

Thus Far I can't ping 192.168.XXX.103 from PC1 & I can't ping 192.168.XXX.101 from PC2. (unreachable)
I have an internet connection on PC1 (of course)

So what I'm I doing wrong or missing ???

---

### Post by luceerose on 2010-05-28
Ever have one of those threads that just goes completely unanswered ?...

The reason I was after this kind of setup was so I could play with PC1's firewall rules to allow ssh on my LAN. The only kind of network traffic that ever goes between my computers is ssh & a shared printer on :631

In which case, is it even necessary for me to have a server acting as hardware firewall ?

---

### Post by Iowan on 2010-05-28
Not absolutely sure - but it would seem that eth1 would need the masquerade instead of eth0.

Another post sneaked in whilst I was head-scratching...
I was kinda wondering about the configuration, but I use my own network as an education tool, so why not...
Does the router have any firewalling built-in?

Yet another side-note... curious why pinging won't work. If PC2 can't ping PC1, it can't get to internet through it.:confused:

---

### Post by mituw16 on 2010-05-28
For my network at my house, my ubuntu 10.04 headless server is acting as a full router/gateway/dhcp/firewall for my house network. 

My server has 2 NICS in it, 
eth0 is my LAN that all computers in my house are connected through
eth1 is the WAN NIC that actually gets the internet connection

So my setup is as follows

modem ---> into eth1 ubuntu server ---> out eth0 of ubuntu server ----> switch ----> everything else like computers and WAPS

So, to accomplish this, here is what I did. It can be frustrating, took me a while to figure out the first time too as I was unable to find any comprehensive guide.
(this is all done on a server without gnome)

1. enable ipv4 forwarding in /etc/sysctl.conf
2. *** optional, but recommended **** install dhcp3 server 
3. configure your /etc/network/interfaces so that eth0 has a static ip address of what ever you would like your LAN subnet to be. 
4. configure /etc/network/interfaces so eth1 is either a static ip, or if it gets it through DHCP from your modem, or how ever you get internet, this is different for everyone. 

---NOTE---- the main thing that we're trying to accomplish from the above setup is that the ubuntu server will provide dhcp services for your LAN network, which has to be on a different subnet than your WAN. So, for example, here is ubuntu gateway's etc/network/interfaces file

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#DHCP NIC
auto eth0
iface eth0 inet static
  address               172.69.75.1
  netmask               255.255.255.0
  network               172.69.75.0
  broadcast             172.69.75.255

#INCOMING NIC
auto eth1
iface eth1 inet static
  address               172.69.74.2
  netmask               255.255.255.0
  network               172.69.74.0
  broadcast             172.69.74.255
  gateway                172.69.74.1

```

As you can see in the above example, eth0 is my lan and it is on the 172.9.75.0/24 subnet, while my WAN connection from my modem is on the 172.69.74.0/24 subnet. I also configured my dhcp3-server to provide dhcp address on eth0 in same 172.69.75.0/24 subnetting scheme.

Continuing... after configure dhcp3-server, sysctl.conf, and your /etc/network/interfaces, you should have internet access on other computers on your LAN. 

---NOTE---- 
if you are not connected through a modem that is already NATing your network, then you will want to add this line to iptables. 

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

this is just simply NATing your network. again, if your modem is already doing this then you dont need to do that.

---

### Post by linuxonbute on 2010-05-28
I had a similar setup to the one you want some years ago and had the same problem too.

As mituw16 says, the crucial bit is that nic1 and nic 2 have to be on different subnets.

AFAIK
You can have all your nics on static addresses.

nic1 ( the nic plugged into your router ) has to be on the same subnet as your modem/router with the modem/router ip address being it's gateway address.

nic2 has to to be on a different subnet and all your other Pc's need to be on the same subnet as it is with it's ip address being their gateway address

---

### Post by PatrickMahoney on 2011-02-03
Did you ever get it working? I have a VERY similar problem.

---

