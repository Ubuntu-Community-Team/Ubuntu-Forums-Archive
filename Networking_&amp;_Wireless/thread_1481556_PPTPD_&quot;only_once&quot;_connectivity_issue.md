---
title: "PPTPD &quot;only once&quot; connectivity issue"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by AnrDaemon on 2010-05-12
I'm experiencing somewhat weird issue, when PPP server allow clients to connect only once, right after server restart.
After that, no more connections allowed.
The interesting part I've managed to gather is that ppp interface is not going up in full (i.e. no address assigned), disallowing peers to communicate.
Until comlete server reboot, no further connections from the outside can be established.

The PPTP server is configured to authenticate through winbind.
The IPTABLES rules is a nonisue, they are not dynamically changed and I omit them in the samples to reduce bloating.
Any other place to check for more clues to the issue?

Initial state (the two ppp interfaces is a local test connection, also don't pay attention to 0's in RX/TX fields, it was done for easier diff'ing of the snaps)
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

First connection in progress.
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp2      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

Connection brought up succesfully, peer authenticated and working as expected.
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp2      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.200  P-t-P:192.168.18.200  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

Link shutthing down per client request.
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp2      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 KB)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

Done with disconnect...
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

Redialing immediately...
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp2      Link encap:Point-to-Point Protocol  
          POINTOPOINT NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

No luck... 619 "unable to connect".
```
--- ifconfig ---
eth0      Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.18.1  Bcast:192.168.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

eth0:10   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.10.2  Bcast:192.168.10.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0:17   Link encap:Ethernet  HWaddr 00:20:ed:7e:98:5a  
          inet addr:192.168.17.2  Bcast:192.168.17.15  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0 KB)  TX bytes:0 (0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.201  P-t-P:192.168.18.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:192.168.18.1  P-t-P:192.168.18.201  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:0 (0 B)  TX bytes:0 (0 B)


--- route ---
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.18.201  *               255.255.255.255 UH    0      0        0 ppp1
ns.ccenter.lan  *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.248 U     0      0        0 eth0
192.168.17.0    *               255.255.255.240 U     0      0        0 eth0
192.168.18.0    *               255.255.255.0   U     0      0        0 eth0
default         192.168.10.1    0.0.0.0         UG    100    0        0 eth0

--- resolv.conf ---
domain ccenter.lan
search ccenter.lan
nameserver 192.168.18.1
```

---

