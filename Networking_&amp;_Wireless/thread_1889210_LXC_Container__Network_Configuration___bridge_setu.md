---
title: "LXC Container / Network Configuration /  bridge setup"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by svtguy88 on 2011-11-30
Alright, I'm trying to set up LXC containers on my system.  For those unfamiliar, it's sort of a virtual machine, but not really.  Anyway, the network configuration for LXC relies on the "virtual machine" communicating through a network bridge.  I've spent the past few days reading online, but I can't, for the life of me, get full network access inside the container.

_Here's what I *can* do:_

-ping and ssh into the container from my host machine at the IP address that I've assigned it (192.168.80.2)

-ssh to my host machine from inside the container (this is accomplished by either using the lxc-console to ssh to the host at 192.168.80.1, or by ssh'ing to the container, and then back to the host)

_Here's what *doesn't* work:_

I can't access the internet from inside the container.  Issuing a wget results in an error that complains that the domain can't be resolved (the same happens if I enter an actual IP address, so it's not just a DNS problem).

Furthermore, I can't access other parts of the network from inside the container.  For example, the container's IP is 192.168.80.2, and if I try to ssh to another machine that is at 192.168.40.1, it gives me "network is unreachable."  The same is true from the other end:  I can't ping or ssh into the container from another machine (other than the host machine).


The configuration for my system is below.  Note that these are the config files from the host side (nothing from inside the LXC containers), as it appears that the container is connecting to the bridge fine (I can ssh into the container from the host), but the bridge isn't getting to the other subnets or the external ethernet interface.

_/etc/network/interfaces:_
```

auto lo eth4 eth3 eth2 eth1 eth0 br0

#loopback
iface lo inet loopback

#set up external (internet) interface
iface eth4 inet dhcp
	
	

#set up internal (network) interface
iface eth3 inet static
	address 192.168.40.1
	netmask 255.255.255.0
	broadcast 192.168.40.255
	network 192.168.40.0
	gateway 192.168.40.1

iface eth2 inet static
	address 192.168.30.1
	netmask 255.255.255.0
	broadcast 192.168.30.255
	network 192.168.30.0
	gateway 192.168.30.1

iface eth1 inet static
	address 192.168.20.1
	netmask 255.255.255.0
	broadcast 192.168.20.255
	network 192.168.20.0
	gateway 192.168.20.1

iface eth0 inet static
	address 192.168.10.1
	netmask 255.255.255.0
	broadcast 192.168.10.255
	network 192.168.10.0
	gateway 192.168.10.1

	
#wireless
#iface wlan0 inet static
#	address 192.168.90.1
#	netmask 255.255.255.0
#	broadcast 192.168.90.255
#	network 192.168.90.0
	#wireless-mode ad-hoc
        #wireless-essid PoopDeck
	#channel 11
	#wireless-key 12345

#bridge for LXC
iface br0 inet static
	address 192.168.80.1
	netmask 255.255.255.0
	broadcast 192.168.80.255
	network 192.168.80.0
	gateway 192.168.80.1	
	bridge_maxwait 0
```

_*output:* ip route_
```
default via 174.102.192.1 dev eth4  metric 100
169.254.0.0/16 dev eth4  scope link  metric 1000
174.102.192.0/19 dev eth4  proto kernel  scope link  src 174.102.217.33
192.168.10.0/24 dev eth0  proto kernel  scope link  src 192.168.10.1
192.168.20.0/24 dev eth1  proto kernel  scope link  src 192.168.20.1
192.168.30.0/24 dev eth2  proto kernel  scope link  src 192.168.30.1
192.168.40.0/24 dev eth3  proto kernel  scope link  src 192.168.40.1
192.168.80.0/24 dev br0  proto kernel  scope link  src 192.168.80.1 
```

_*output:* route n_
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         174.102.192.1   0.0.0.0         UG    100    0        0 eth4
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth4
174.102.192.0   0.0.0.0         255.255.224.0   U     0      0        0 eth4
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.40.0    0.0.0.0         255.255.255.0   U     0      0        0 eth3
192.168.80.0    0.0.0.0         255.255.255.0   U     0      0        0 br0
```


_*output:* ip link_
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:14 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:15 brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:16 brd ff:ff:ff:ff:ff:ff
5: eth3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:17 brd ff:ff:ff:ff:ff:ff
6: eth4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 576 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0f:1f:fa:51:33 brd ff:ff:ff:ff:ff:ff
7: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:13:f7:3b:2c:7c brd ff:ff:ff:ff:ff:ff
10: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether 92:44:1c:32:07:06 brd ff:ff:ff:ff:ff:ff
12: vethTu1nnI: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000
    link/ether 92:44:1c:32:07:06 brd ff:ff:ff:ff:ff:ff
```

_*output:* ip addr_
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:14 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.1/24 brd 192.168.10.255 scope global eth0
    inet6 fe80::204:23ff:fe09:6a14/64 scope link
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:15 brd ff:ff:ff:ff:ff:ff
    inet 192.168.20.1/24 brd 192.168.20.255 scope global eth1
    inet6 fe80::204:23ff:fe09:6a15/64 scope link
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:16 brd ff:ff:ff:ff:ff:ff
    inet 192.168.30.1/24 brd 192.168.30.255 scope global eth2
    inet6 fe80::204:23ff:fe09:6a16/64 scope link
       valid_lft forever preferred_lft forever
5: eth3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:04:23:09:6a:17 brd ff:ff:ff:ff:ff:ff
    inet 192.168.40.1/24 brd 192.168.40.255 scope global eth3
    inet6 fe80::204:23ff:fe09:6a17/64 scope link
       valid_lft forever preferred_lft forever
6: eth4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 576 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:0f:1f:fa:51:33 brd ff:ff:ff:ff:ff:ff
    inet 174.102.217.33/19 brd 255.255.255.255 scope global eth4
7: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:13:f7:3b:2c:7c brd ff:ff:ff:ff:ff:ff
10: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether 92:44:1c:32:07:06 brd ff:ff:ff:ff:ff:ff
    inet 192.168.80.1/24 brd 192.168.80.255 scope global br0
    inet6 fe80::9044:1cff:fe32:706/64 scope link
       valid_lft forever preferred_lft forever
12: vethTu1nnI: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000
    link/ether 92:44:1c:32:07:06 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::9044:1cff:fe32:706/64 scope link
       valid_lft forever preferred_lft forever
```

By the way, my system uses Shorewall for a firewall.  It's setup consists of a local zone (eth0-2) a dmz zone (eth3) and net zone (eth4).  It's also setup to masquerade all of the networks to output on eth4, as it connects to my modem.  Let me know if any other configs or outputs could be helpful.  

I'm running out of ideas.

---

### Post by svtguy88 on 2011-12-01
I'll post the answer I found on the LXC mailing list, In case someone else runs into a problem like this.

The issue was that inside my container, there was no default gateway assigned.  I added "route add default gw 192.168.80.1" to the container's startup scrips (192.168.80.1 is the address of my bridge, br0), and now everthing works great.

---

