---
title: "Unable to browse pages through wifi"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by aacool on 2009-08-15
Hi,

I've just installed Ubuntu on my new Atom-based PC. I'm using a Netgear WG111 USB adapter for WiFi and it is able to connect to my wifi network. No web pages are opening, however. I am also not able to ping my router on 192.168.1.1. Other machines on my network, including Ubuntu machines are browsing sites just fine.

Any help will be appreciated. Please let me know if more details are needed:popcorn:

---

### Post by superprash2003 on 2009-08-15
post output of
1)ping 208.67.222.222
2)ping google.com
3)ifconfig

---

### Post by aacool on 2009-08-18
Info below. Pl note the Machine gets a valid IP address (192.168.1.5) from the router but is unable to ping the router at 192.168.1.1

post output of
1)ping 208.67.222.222
ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
^C
--- 208.67.222.222 ping statistics ---
32 packets transmitted, 0 received, 100% packet loss, time 31168ms


2)ping google.com
same
3)ifconfig
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:d6:81:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28994 (28.9 KB)  TX bytes:28994 (28.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:2a:d7:35:d3  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:fed7:35d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5529 (5.5 KB)  TX bytes:25316 (25.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-2A-D7-35-D3-35-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 lsusb
Bus 001 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B]
Bus 001 Device 002: ID 0d49:7410 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
^C
--- 192.168.1.1 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8061ms

---

### Post by superprash2003 on 2009-08-18
post output of** route -n** , also try typing** sudo ifdown eth0** and** sudo ifdown wmaster0** and then try pinging your router

---

