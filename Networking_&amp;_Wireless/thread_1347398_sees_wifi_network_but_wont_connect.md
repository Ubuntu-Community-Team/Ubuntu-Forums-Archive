---
title: "sees wifi network but wont connect"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by scuba117 on 2009-12-06
[SIZE=2]I have a Linksys WUSB600N wireless adapter for my Linux Ubuntu system, and it says it is connected to the network yet it wont let me get on the internet..[/SIZE]

[SIZE=1]
root@ubuntu:/home/# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0d:9d:54:9a:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e3:a7:78  
          inet6 addr: fe80::21e:e5ff:fee3:a778/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126 (126.0 B)  TX bytes:2036 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-E3-A7-78-65-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/home/#

root@ubuntu:/home/sknight# ifdown wmaster0
ifdown: interface wmaster0 not configured
root@ubuntu:/home/sknight# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/SIZE]

---

