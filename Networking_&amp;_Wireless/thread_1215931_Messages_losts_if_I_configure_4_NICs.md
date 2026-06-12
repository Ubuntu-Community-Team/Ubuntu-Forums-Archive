---
title: "Messages losts if I configure 4 NICs"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by mr.josep on 2009-07-17
Hi:
I need to have 4 NICs configured on my system on different subnets.
All are configured with static IPs and using /etc/network/interfaces.
I haven't Network Manager installed.
When I comment 2 NICs on interface file, the remaining 2 NICs works properly.
When I uncomment all NICs configuration, only the firsts 2 works properly: the other 2 'lost' all messages:
-- ifconfing shows the 4 NICs configured and with the assigned IP.
-- I can put programs to LISTEN on the IP of every NIC (netstat shows the LISTEN state)
-- If I test to connect to 2 last NICs, ifconfig shows that some messages are arrived, but the program does not ends the listen() call: It seems that the messages are lost.

On the following 'screenshots', interface eth7 does not works (losts its messages), but if I comment the entry for eth0 or eth2, eth7 works properly

Any help would be appreciated.

-------------------------Interfaces file----------------
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.7
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 192.168.1.7
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1

auto eth7
iface eth7 inet static
address 192.168.2.7
netmask 255.255.255.0

auto eth8
iface eth8 inet static
address 192.168.3.7
netmask 255.255.255.0
-----------------------end interfaces--------------------

---------------------------ifconfig -a ----------------------
eth0      Link encap:Ethernet  HWaddr 00:21:70:4e:e3:c0
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fe4e:e3c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37842331 (37.8 MB)  TX bytes:24124438 (24.1 MB)
          Interrupt:247 Base address:0x4000

eth2      Link encap:Ethernet  HWaddr 00:80:5a:69:b4:4f
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe69:b44f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1034956 (1.0 MB)  TX bytes:314551 (314.5 KB)
          Interrupt:17 Base address:0x6c00

eth7      Link encap:Ethernet  HWaddr 00:1b:21:3b:53:af
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe3b:53af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:938 (938.0 B)  TX bytes:22534 (22.5 KB)
          Memory:fe7e0000-fe800000

eth8      Link encap:Ethernet  HWaddr 00:1b:21:3d:e4:c5
          inet addr:192.168.3.7  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe8e0000-fe900000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:371795 (371.7 KB)  TX bytes:371795 (371.7 KB)

pan0      Link encap:Ethernet  HWaddr c6:de:56:4a:d8:6d
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
-----------------------end ifconfig ----------------------------------

---

### Post by mr.josep on 2009-07-18
Please, any one can help me?.
Thanks

---

