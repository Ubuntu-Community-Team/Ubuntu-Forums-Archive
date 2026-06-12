---
title: "problem with bonding eth4 to eth7"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by johanneskoester on 2012-04-03
We have a server with a Gigabit copper network card eth0,
and 4 fibre network cards eth4 -- eth7, which we want to use bonded as bond0.
When we bring up the server without bonding, everything looks fine.
(It is expected that eth1, eth2, eth3 do not exist)

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:01 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:03 brd ff:ff:ff:ff:ff:ff
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether d0:67:e5:f9:b9:05 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.21/21 brd 10.90.135.255 scope global eth0
    inet6 fe80::d267:e5ff:fef9:b905/64 scope link 
       valid_lft forever preferred_lft forever
5: eth3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:07 brd ff:ff:ff:ff:ff:ff
6: eth4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 90:e2:ba:04:71:74 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.22/21 brd 10.90.135.255 scope global eth4
    inet6 fe80::92e2:baff:fe04:7174/64 scope link 
       valid_lft forever preferred_lft forever
7: eth5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 90:e2:ba:04:71:75 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.23/21 brd 10.90.135.255 scope global eth5
    inet6 fe80::92e2:baff:fe04:7175/64 scope link 
       valid_lft forever preferred_lft forever
8: eth6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 90:e2:ba:04:77:b0 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.24/21 brd 10.90.135.255 scope global eth6
    inet6 fe80::92e2:baff:fe04:77b0/64 scope link 
       valid_lft forever preferred_lft forever
9: eth7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether 90:e2:ba:04:77:b1 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.25/21 brd 10.90.135.255 scope global eth7
    inet6 fe80::92e2:baff:fe04:77b1/64 scope link 
       valid_lft forever preferred_lft forever

```


However, if we boot with the bonding configuration (/etc/network/interfaces as shown below), it does seems not to work.
Especially note that there are 0 packets going across the IP.
However, we can still login on the assigned IP without problems.
So in fact, it works, but the system does not recognize it.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


auto bond0
iface bond0 inet static
	address 10.90.129.22
	netmask 255.255.248.0
	network 10.90.128.0
	broadcast 10.90.135.255
	gateway 10.90.135.254
	slaves eth4 eth5 eth6 eth7
	bond_mode 0
	bond_miimon 100
	bond_updelay 200
	bond_downdelay 200


auto eth0
iface eth0 inet static
	address 10.90.129.21
	netmask 255.255.248.0
	network 10.90.128.0
	broadcast 10.90.135.255
	gateway 10.90.135.254


```


This is the result of ifconfig:
```

bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:10.90.129.22  Bcast:10.90.135.255  Mask:255.255.248.0
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr d0:67:e5:f9:b9:05  
          inet addr:10.90.129.21  Bcast:10.90.135.255  Mask:255.255.248.0
          inet6 addr: fe80::d267:e5ff:fef9:b905/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87669 (87.6 KB)  TX bytes:133927 (133.9 KB)
          Interrupt:28 Memory:ea000000-ea012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19463 (19.4 KB)  TX bytes:19463 (19.4 KB)

```

This is the result of "ip address show":
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:01 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:03 brd ff:ff:ff:ff:ff:ff
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether d0:67:e5:f9:b9:05 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.21/21 brd 10.90.135.255 scope global eth0
    inet6 fe80::d267:e5ff:fef9:b905/64 scope link 
       valid_lft forever preferred_lft forever
5: eth3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether d0:67:e5:f9:b9:07 brd ff:ff:ff:ff:ff:ff
6: eth4: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 90:e2:ba:04:71:74 brd ff:ff:ff:ff:ff:ff
7: eth5: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 90:e2:ba:04:71:75 brd ff:ff:ff:ff:ff:ff
8: eth6: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 90:e2:ba:04:77:b0 brd ff:ff:ff:ff:ff:ff
9: eth7: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 90:e2:ba:04:77:b1 brd ff:ff:ff:ff:ff:ff
10: bond0: <NO-CARRIER,BROADCAST,MULTICAST,MASTER,UP> mtu 1500 qdisc noqueue state DOWN 
    link/ether 00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.22/21 brd 10.90.135.255 scope global bond0

```

As you see, the state of bond0 is DOWN, and eth4--eth4 are not recognized as SLAVE.

Nevertheless, I can log in an am greeted as follows.
```

Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-17-server x86_64)

 * Documentation:  [https://help.ubuntu.com/11.10/serverguide/C](https://help.ubuntu.com/11.10/serverguide/C)

  System information as of Tue Apr  3 19:14:10 CEST 2012

  System load:  0.08               Processes:            334
  Usage of /:   16.7% of 45.66GB   Users logged in:      1
  Memory usage: 0%                 IP address for eth0:  10.90.129.21
  Swap usage:   0%                 IP address for bond0: 10.90.129.22

```
Note that bond0 and the correct IP are reported here.



On another server, I see the following if ifconfig and ip address show, as it should be. 
The servers have the same OS and configuration.



```

bond0     Link encap:Ethernet  HWaddr 90:e2:ba:04:78:98  
          inet addr:10.90.129.12  Bcast:10.90.135.255  Mask:255.255.248.0
          inet6 addr: fe80::92e2:baff:fe04:7898/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:2923964 errors:0 dropped:24 overruns:0 frame:0
          TX packets:5707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:659482850 (659.4 MB)  TX bytes:1245784 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr d0:67:e5:f9:28:cb  
          inet addr:10.90.129.11  Bcast:10.90.135.255  Mask:255.255.248.0
          inet6 addr: fe80::d267:e5ff:fef9:28cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:615594367 errors:0 dropped:12 overruns:0 frame:0
          TX packets:676110210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660877633956 (660.8 GB)  TX bytes:711681474661 (711.6 GB)
          Interrupt:24 Memory:e6000000-e6012800 

eth4      Link encap:Ethernet  HWaddr 90:e2:ba:04:78:98  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1461982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329743074 (329.7 MB)  TX bytes:621259 (621.2 KB)

eth5      Link encap:Ethernet  HWaddr 90:e2:ba:04:78:98  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1461982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329739776 (329.7 MB)  TX bytes:624525 (624.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:955920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:955920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:246598316 (246.5 MB)  TX bytes:246598316 (246.5 MB)

```

Here only eth4 and eth5 exist, but as you can see, they are marked as SLAVE, and bonding works just fine.

ip address show for bond0; state is UP:
```

8: bond0: <BROADCAST,MULTICAST,MASTER,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP 
    link/ether 90:e2:ba:04:78:98 brd ff:ff:ff:ff:ff:ff
    inet 10.90.129.12/21 brd 10.90.135.255 scope global bond0
    inet6 fe80::92e2:baff:fe04:7898/64 scope link 
       valid_lft forever preferred_lft forever

```

Any ideas?
The most puzzling thing is that the .22 IP is reachable and works just fine for logins, but the system claims that bond0 is down, as are all eth*.

---

