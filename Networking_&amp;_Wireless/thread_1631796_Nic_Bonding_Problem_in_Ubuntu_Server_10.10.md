---
title: "Nic Bonding Problem in Ubuntu Server 10.10"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by Tobeus on 2010-11-27
Okay, what I'm trying to do is to bond my 2 network interfaces for failover / load balancing.  I have been able to configure the bond0 interface using a static IP, but I when I pull the plug on the primary interface, it does not fail over to the secondary interface.

My /etc/network/interfaces file:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
 iface bond0 inet static
 address 192.168.16.30
 netmask 255.255.255.0
 gateway 192.168.16.50
 bond-slaves none
 bond-mode 1
 bond-miimon 100
 post-up ifenslave bond0 eth0 eth1
 pre-down ifenslave -d bond0 eth0 eth1

auto eth0
iface eth0 inet manual
 bond-master bond0
 bond-primary eth0 eth1

auto eth1
iface eth1 inet manual
 bond-master bond0
 bond-primary eth0 eth1
```

I also added this to my /etc/modprobe.d/aliases.conf
```
alias bond0 bonding
options mode=1 miimon=100 downdelay=200 updelay=200
```

And added this to my /etc/modules
```
# This enables nic bonding
bonding mode=1 miimon=100 primary=eth0
```

I have installed ifenslave and can connect through ssh to the primary ip address.  However, if the primary eth0 card is disconnected manually, the eth1 card does not take over.

When I type ifconfig in a terminal, I get:
```
bond0     Link encap:Ethernet  HWaddr 00:1a:a0:c8:3d:49  
          inet addr:192.168.16.30  Bcast:192.168.16.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fec8:3d49/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40292 (40.2 KB)  TX bytes:20700 (20.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1a:a0:c8:3d:49  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:155 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40292 (40.2 KB)  TX bytes:20700 (20.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44933 (44.9 KB)  TX bytes:44933 (44.9 KB)

virbr0    Link encap:Ethernet  HWaddr da:5c:75:7d:8a:47  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::d85c:75ff:fe7d:8a47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```  

I see eth0 configured here, but not eth1.  Not sure if I am doing something wrong.  Any help is appreciated!

---

### Post by Thylex on 2011-12-20
I dunno if you solved this already, but I'll answer anyway.

Bonding changed in 10.04 and you have configured your system somewhere inbetween the old and new ways.

You can find a good guide here [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding) just be sure to read what applies for 10.04 and after and not the sections on pre-10.04.

Basically what you need to do is remove the entries from /etc/modprobe.conf and all other files. It's all done from the interfaces file now.
In your case your interfaces file should look something like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
 address 192.168.16.30
 netmask 255.255.255.0
 gateway 192.168.16.50
 bond-slaves eth0 eth1
 bond-mode 1
 bond-miimon 100


```Note that there is no iface entries for eth0 and eth1 and there shouldn't be.

Also, I would advise you to move from miimon checks to using arp instead. Miimon just checks that there is link on the NIC, and I have seen many, many cases where the ports in the switches have refused traffic for any number of reasons but still had link up. Setting arp checks with your default gateway as the arp-target is usually a much better way to check if the NIC is working or not.

---

