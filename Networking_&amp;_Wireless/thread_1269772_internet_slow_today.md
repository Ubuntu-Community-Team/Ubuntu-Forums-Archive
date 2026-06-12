---
title: "internet slow today"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Rainbowsix on 2009-09-18
I tried to enable internet connection sharing by using the steps here:
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

It caused problems for me, so I removed the packages and flushed ipconfig. Today, the internet seemed slow so I tried speedtest.net

My result was only about 3mbps, less than half of my average of 6.5mbps.

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:19:66:e5:78:f1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27824 (27.8 KB)  TX bytes:27824 (27.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:1d:93:52:07  
          inet addr:192.168.0.142  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe93:5207/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24701 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36750613 (36.7 MB)  TX bytes:5240834 (5.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-1D-93-52-07-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Skooter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:F0:F7:46:A1   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


---

