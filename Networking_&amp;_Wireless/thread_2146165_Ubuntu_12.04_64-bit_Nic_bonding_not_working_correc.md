---
title: "Ubuntu 12.04 64-bit Nic bonding not working correctly"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by UclaGeek on 2013-05-17
Hi guys, 

I've been trying to get 2 Nic's bonded in balance-alb mode and for the life of me I can not figure out what's causing it to not work. 

Here's my /etc/network/interfaces 

```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet manual
   bond-master bond0


auto eth1
iface eth0 inet manual
   bond-master bond0


auto bond0
iface bond0 inet static
    address 192.168.1.3
    netmask 255.255.255.0
    gateway 192.168.1.1
    bond-slaves none
    bond-miimon 100
    bond-mode balance-alb

```

ifconfig shows an interface called "rename" I've never seen that before. 

```

bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 00:16:76:bf:47:d6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:febf:47d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348876 (348.8 KB)  TX bytes:407453 (407.4 KB)
          Interrupt:21 Memory:dffe0000-e0000000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:259064 (259.0 KB)  TX bytes:259064 (259.0 KB)


rename2   Link encap:Ethernet  HWaddr 00:16:76:bf:47:d6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:febf:47d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55048 (55.0 KB)  TX bytes:14962 (14.9 KB)
          Interrupt:17 Base address:0x8f00 

```

When I do cat /proc/net/bonding/bond0 I get this:

```

Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: None
MII Status: down
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

```

I've been trying to figure this out for almost a week and I just can't seem to find the issue. 

Any help is greatly appreciated.

---

### Post by praseodym on 2013-05-17
Check:
```

cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by UclaGeek on 2013-05-20
I had to make changes just to get the network to start working. 

my [COLOR=#000000]/etc/network/interfaces
[/COLOR]
```


# The loopback network interfaceauto lo
iface lo inet loopback


# bond0 is the bonded NIC and can be used like any other normal NIC.
# bond0 is configured using static network information.
auto bond0
iface bond0 inet static
        address 192.168.1.3
        gateway 192.168.1.1
        netmask 255.255.255.0
        dns-nameservers 8.8.8.8 8.8.4.4
        bond-mode 6
        bond-miimon  100
        bond-slaves eth0 eth1


# The primary network interface
auto eth0
iface eth0 inet manual
        bond-master bond0


auto eth1
iface eth1 inet manual
        bond-master bond0

```

ifconfig

```

bond0     Link encap:Ethernet  HWaddr 00:16:76:bf:47:d6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:febf:47d6/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:116309394 errors:0 dropped:391 overruns:0 frame:0
          TX packets:89962808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113940423288 (113.9 GB)  TX bytes:82465223406 (82.4 GB)


eth1      Link encap:Ethernet  HWaddr 00:16:76:bf:47:d6  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:116309394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89962808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113940423288 (113.9 GB)  TX bytes:82465223406 (82.4 GB)
          Interrupt:21 Memory:dffe0000-e0000000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:392218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:161678007 (161.6 MB)  TX bytes:161678007 (161.6 MB)

```

cat /proc/net/bonding/bond0

```

Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)


Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: eth1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0


Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:16:76:bf:47:d6
Slave queue ID: 0

```

and [LEFT][COLOR=#000000][FONT=Ubuntu Mono]cat /etc/udev/rules.d/70-persistent-net.rules


[/FONT][/COLOR][/LEFT]
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:76:bf:47:d6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:04:05.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:d1:1d:7c:80", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

---

### Post by eskorsta on 2013-09-03
Have you managed to fix this problem? I've got exactly the same situation over here...

---

### Post by freesbee on 2014-07-22
Sorry for posting in an old thread, but was having 90% a similar problem. Of course i will open a new thread if that is the case.
My distro is 12.04.4 x86_64, system is absolutely clean fresh install.
I wrote and documented everything very carefully, and at the last restart for the final testing of what I was writing, suddenly the bond0 came up, so I had to rewrite the entire post :confused:

I've been struggling like hell for one week with the bond0 not coming up till when I specified **[FONT=Courier New][COLOR=#FF0000]bond-slaves none[/COLOR][/FONT]** in my **/etc/network/interfaces**
 which now looks like this:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual
bond-master bond0
bond-primary eth0

auto eth1
iface eth1 inet manual
bond-master bond0

auto bond0
iface bond0 inet static
address [mySubnet].53
gateway [mySubnet].1
netmask 255.255.255.0
dns-nameservers [mySubnet].50
bond-mode 0
[COLOR=#FF0000]bond-slaves none[/COLOR]
bond-miimon 100
bond-lacp-rate 1 

```

As long as my entry was **[FONT=Courier New]bond-slaves eth0 eth1[/FONT]** I had no chance to get my bond0 interface transmitting anything (I could ping it from the console, but that was all). Is that line really the reason why my bond0 did not come up?

Secondly: if my **/proc/net/bonding/bond0** looks like this

```

Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eth0
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 00:1c:c0:9c:35:e7
Slave queue ID: 0

Slave Interface: eth1
MII Status: up
Speed: 1000 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 68:05:ca:28:b6:d2
Slave queue ID: 0 

```

and my **ifconfig** outputs is

```

bond0     Link encap:Ethernet  HWaddr 00:1c:c0:9c:35:e7  
          inet addr:192.168.0.53  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe9c:35e7/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:13840 errors:0 dropped:78 overruns:0 frame:0
          TX packets:5764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1293584 (1.2 MB)  TX bytes:2383304 (2.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:9c:35:e7  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:6946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:646679 (646.6 KB)  TX bytes:1206634 (1.2 MB)
          Interrupt:20 Memory:d0700000-d0720000 

eth1      Link encap:Ethernet  HWaddr 00:1c:c0:9c:35:e7  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:6894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:646905 (646.9 KB)  TX bytes:1176670 (1.1 MB)
          Interrupt:19 Memory:d06c0000-d06e0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

how can I be sure that the two NICs are really working together to increase the network capacity of my server?
just copying bulky files and checking the speed?

---

