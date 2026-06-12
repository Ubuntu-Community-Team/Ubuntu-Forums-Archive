---
title: "Static IP for bridge"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-05-18
Hello,

I'm trying to set static IP for my bridge network. But it's strange that it doesn't work. Here is the network/interfaces file:
----------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        address 192.168.0.20
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
------------------

And here is my "ifconfig" result:

------------
br0       Link encap:Ethernet  HWaddr 1c:75:08:c1:b3:f1  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe81::1e75:7ff:fec1:b2f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2232446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:721978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:807868275 (807.8 MB)  TX bytes:4368295291 (4.3 GB)

eth0      Link encap:Ethernet  HWaddr 1c:75:08:c1:b3:f1  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2237417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3473206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848474591 (848.4 MB)  TX bytes:4563900043 (4.5 GB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:422238 (422.2 KB)  TX bytes:422238 (422.2 KB)

virbr0    Link encap:Ethernet  HWaddr 8e:88:18:a2:4c:34  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vnet0     Link encap:Ethernet  HWaddr fe:55:00:a7:36:f4  
          inet6 addr: fe81::fc54:ff:fea7:36f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:55304 (55.3 KB)  TX bytes:96816 (96.8 KB)

vnet1     Link encap:Ethernet  HWaddr fe:55:00:2b:b7:8f  
          inet6 addr: fe81::fc54:ff:fe2b:b78f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:14753 (14.7 KB)  TX bytes:92896 (92.8 KB)


---------------

Please tell me if there's anything wrong. Thank you in advance!

---

