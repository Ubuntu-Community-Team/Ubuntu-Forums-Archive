---
title: "wired network disconnected"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by 007casper on 2009-07-03
ethernet cable is connected.  It tries to connect and then states wired network disconnected.  It used to work. How can I fix this problem?

I was able to use it without a problem at home with internet connection.  It worked flawlessly. 

Then, I took it to the datacenter, and decided to load gadmin-bind. The instructions for gadmin-bind in a pdf suggests
```
sudo /etc/init.d/apparmor stop
```

then, I went to synaptic to load gadmin-bind, and realized I didnt have internet connection.  I kept selecting the ethernet connection Auth01, and it will spin for a while and state "wired network disconnected"

It used to work at home, but I had linksys attached to it. In the datacenter I am not using linksys, and I have a static IP. I am hooking up the ethernet cable directly to the server.

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:90  
          inet addr:208.150.220.126  Bcast:208.150.220.255  Mask:255.255.255.210
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfa0000-fdfc0000 

eth1      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:91  
          inet6 addr: fe80::21f:c6ff:fed5:b991/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4320 (4.3 KB)  TX bytes:2178 (2.1 KB)
          Memory:fdfe0000-fe000000 

eth2      Link encap:Ethernet  HWaddr 00:1f:c6:d6:04:4a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdae0000-fdb00000 

eth3      Link encap:Ethernet  HWaddr 00:1f:c6:d6:03:76  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fd9e0000-fda00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12100 (12.1 KB)  TX bytes:12100 (12.1 KB)

```

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:90  
          inet addr:208.150.220.126  Bcast:208.150.220.255 Mask:255.255.255.210
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfa0000-fdfc0000 

eth1      Link encap:Ethernet  HWaddr 00:1f:c6:d5:b9:91  
          inet6 addr: fe80::21f:c6ff:fed5:b991/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:7560 (7.5 KB)  TX bytes:10386 (10.3 KB)
          Memory:fdfe0000-fe000000 

eth2      Link encap:Ethernet  HWaddr 00:1f:c6:d6:04:4a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdae0000-fdb00000 

eth3      Link encap:Ethernet  HWaddr 00:1f:c6:d6:03:76  
          inet6 addr: fe80::21f:c6ff:fed6:376/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)
          Memory:fd9e0000-fda00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26960 (26.9 KB)  TX bytes:26960 (26.9 KB)

pan0      Link encap:Ethernet  HWaddr ce:ae:41:1c:41:4f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 208.150.220.126
	netmask 255.255.255.210
	network 208.150.220.124
	broadcast 208.150.220.255
	gateway 208.150.220.125
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 208.150.210.10 208.150.218.10
	dns-search example.com
``` 

```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
208.150.220.124 0.0.0.0         255.255.255.210 U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         208.150.220.125 0.0.0.0         UG        0 0          0 eth0
```

I try to ping my static IP, it returned...
Do you want to ping broadcast? Then -b

Why is it showing as wired network disconnected? How can I make it work?

---

### Post by 007casper on 2009-07-03
*bump*

---

### Post by 007casper on 2009-07-03
I checked [network configuration page]("https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html")

The example shows that /etc/network/interfaces 
> 
iface eth1 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	gateway 192.168.0.1

/etc/resolv.conf
> 
search mydomain.example
nameserver 192.168.0.1
nameserver 4.2.2.2

how come nameserver has 192.198.0.1 and at the same time same IP for gateway?

???

I really would appreciate any help.  I need to figure this out. What is wrong with my set up?

Thanks

---

### Post by 007casper on 2009-07-04
I hear the grasshoppers chirping.

anybody ~ any ideas why I cant get a connection :-(

---

### Post by 007casper on 2009-07-04
```
lspci
*snip*
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
*snip*
07:00.0 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)
07:00.1 Ethernet controller: Intel Corporation 80003ES2LAN Gigabit Ethernet Controller (Copper) (rev 01)

```

```
[    5.510383] 0000:07:00.0: eth0: (PCI Express:2.5GB/s:Width x4) 00:1f:c6:d5:b9:90
[    5.510386] 0000:07:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.510464] 0000:07:00.0: eth0: MAC: 4, PHY: 5, PBA No: ffffff-0ff

[    5.625794] 0000:07:00.1: eth1: (PCI Express:2.5GB/s:Width x4) 00:1f:c6:d5:b9:91
[    5.625796] 0000:07:00.1: eth1: Intel(R) PRO/1000 Network Connection
[    5.625874] 0000:07:00.1: eth1: MAC: 4, PHY: 5, PBA No: ffffff-0ff

[    5.788957] 0000:03:00.0: eth2: (PCI Express:2.5GB/s:Width x1) 00:1f:c6:d6:04:4a
[    5.788959] 0000:03:00.0: eth2: Intel(R) PRO/1000 Network Connection
[    5.789042] 0000:03:00.0: eth2: MAC: 2, PHY: 2, PBA No: ffffff-0ff

[    5.944211] 0000:02:00.0: eth3: (PCI Express:2.5GB/s:Width x1) 00:1f:c6:d6:03:76
[    5.944213] 0000:02:00.0: eth3: Intel(R) PRO/1000 Network Connection
[    5.944297] 0000:02:00.0: eth3: MAC: 2, PHY: 2, PBA No: ffffff-0ff

[   29.513951] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.165329] type=1503 audit(1246690801.416:12): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=107 name="/var/lib/named/etc/bind/named.conf" pid=2866 profile="/usr/sbin/named"
[   41.005799] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   41.005801] Bluetooth: BNEP filters: protocol multicast
[   41.012315] Bridge firewalling registered
[   41.781310] ppdev: user-space parallel port driver
[   42.083376] warning: `proftpd' uses 32-bit capabilities (legacy support in use)
[   45.760964] e1000e 0000:02:00.0: irq 2293 for MSI/MSI-X
[   45.820111] e1000e 0000:02:00.0: irq 2293 for MSI/MSI-X
[   45.822431] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   45.840937] e1000e 0000:03:00.0: irq 2294 for MSI/MSI-X
[   45.900708] e1000e 0000:03:00.0: irq 2294 for MSI/MSI-X
[   45.902622] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   45.952547] e1000e 0000:07:00.1: irq 2295 for MSI/MSI-X
[   46.011970] e1000e 0000:07:00.1: irq 2295 for MSI/MSI-X
[   46.014531] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   48.682503] 0000:02:00.0: eth3: Link is Up 100 Mbps Full Duplex, Flow Control: None
[   48.682507] 0000:02:00.0: eth3: 10/100 speed: disabling TSO
[   48.683641] ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[   58.881881] eth3: no IPv6 routers present
[  461.990134] 0000:02:00.0: eth3: Link is Down
[  466.756064] 0000:07:00.1: eth1: Link is Up 100 Mbps Full Duplex, Flow Control: None
[  466.756068] 0000:07:00.1: eth1: 10/100 speed: disabling TSO
[  466.757128] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  477.190008] eth1: no IPv6 routers present
[ 1016.848752] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 1188.385944] keyboard.c: can't emulate rawmode for keycode 240
[ 1188.630012] keyboard.c: can't emulate rawmode for keycode 240
[ 1188.881987] keyboard.c: can't emulate rawmode for keycode 240
[ 1454.604391] device eth0 entered promiscuous mode
[ 1454.712519] device eth0 left promiscuous mode
[ 1508.370646] device eth0 entered promiscuous mode
[ 1547.210637] device eth0 left promiscuous mode
[ 1766.746287] e1000e 0000:07:00.0: irq 2296 for MSI/MSI-X
[ 1766.801342] e1000e 0000:07:00.0: irq 2296 for MSI/MSI-X
[ 1766.804006] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2057.554434] e1000e 0000:07:00.1: irq 2295 for MSI/MSI-X
[ 2057.611344] e1000e 0000:07:00.1: irq 2295 for MSI/MSI-X
[ 2057.614054] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2059.966065] 0000:07:00.1: eth1: Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 2059.966068] 0000:07:00.1: eth1: 10/100 speed: disabling TSO
[ 2059.967157] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 2070.390010] eth1: no IPv6 routers present

```

```
sudo tcpdump -vvxXns0 -i eth0
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
```

```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
```

---

### Post by Iowan on 2009-07-04
> **007casper said:**
> 
how come nameserver has 192.198.0.1 and at the same time same IP for gateway? My router is my DHCP server, DNS server, and gateway.
The machine actually has four ethernet ports? 
I suppose you noticed that eth1 is not getting the address you assigned?
Short term, you might try using **ifconfig** to manually assign an address to eth1. (You'll need to consult **man ifconfig** for details).

---

### Post by 007casper on 2009-07-04
> My router is my DHCP server, DNS server, and gateway.
same IP like the example on post number 3 :shock:

Yes, I have 4 ports.  Gig LAN connection.  I thought about hooking up the  connection straight to the server without a router, by assigning the static IP through /etc/network/interfaces.

It just wouldnt work.  Maybe server ports like routers, and not straight connections.  Is that possible?  I just didnt want to deal with cycling routers every now and then.

I looked at man ifconfig, and many other threads in the forum.  I just dont understand why it stopped working. It used to work with all the bells and whistles when it was in a network.  Now it is just moody.  eth1 just wont budge. It hangs, or doesnt work at all.

---

