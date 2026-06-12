---
title: "Port Forwarding to VPN Client (kvpnc)"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by TakeshiKovacs on 2010-03-09
Hi guys,

I could use some help with this. I set up an ssh server and configured port forwarding on my router so that I can access the ssh server from the internet. This is working fine, also from within the LAN.

Additionally this machine should be connected to an VPN Server on the internet. Again, this is working. I get connected, the tun interface is coming up, etc.

The moment the VPN Connection is established I can not connect to the SSH Server anymore from the internet, LAN ist still working fine. I guess it has something to do with the route that is set by the VPN Connection?!

So my question is, what do I have to do to reach the ssh server from the internet while the ssh server is connected to an VPN Server itself.

ifconfig without VPN

```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:c4:df:80  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fec4:df80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226651706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358501666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:839414562 (839.4 MB)  TX bytes:3397073079 (3.3 GB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19017181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19017181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1121981201 (1.1 GB)  TX bytes:1121981201 (1.1 GB)

```

ifconfig with VPN
```

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:c4:df:80  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fec4:df80/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226729362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358609053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:853655102 (853.6 MB)  TX bytes:3454566049 (3.4 GB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19019142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19019142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1122096245 (1.1 GB)  TX bytes:1122096245 (1.1 GB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.0.32.34  P-t-P:10.0.32.33  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1017 (1.0 KB)  TX bytes:1119 (1.1 KB)
```

route without VPN

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```

route with VPN
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.32.69      *               255.255.255.255 UH    0      0        0 tun0
10.0.32.1       10.0.32.69      255.255.255.255 UGH   0      0        0 tun0
rotterdam.perfe 192.168.2.1     255.255.255.255 UGH   0      0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth0
default         10.0.32.69      128.0.0.0       UG    0      0        0 tun0
128.0.0.0       10.0.32.69      128.0.0.0       UG    0      0        0 tun0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```

---

### Post by TakeshiKovacs on 2010-03-11
In addition to the ssh server, the samba services on the machine are also unreachable when connected via VPN.

Anybody with an idea?

---

