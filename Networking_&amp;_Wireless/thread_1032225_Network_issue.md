---
title: "Network issue"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by itsramesh_s on 2009-01-06
Hi,

I have problem with LAN and wireless. 

when connected to LAN works fine, suppose if i  wanted use wireless,after disconnecting LAN cable, still shows same 
IP Address to eth0 and wlan0.

Presently after rebooting, wireless starts working.

How to over come this problem. i tried ifdown eth0.

Thanks in advance  for suggestions!

Regards,
Ramesh.

---

### Post by superprash2003 on 2009-01-06
post output of 
1)ifconfig
2)iwconfig

 you first need to know the right interface for wired and wireless

---

### Post by itsramesh_s on 2009-01-06
Hi,

1)ifconfig output.

eth0      Link encap:Ethernet  HWaddr 00:1e:33:3d:4c:a3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3781694625 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7268 (7.2 KB)  TX bytes:7268 (7.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:49:12:90
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe49:1290/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3776055 (3.7 MB)  TX bytes:1360850 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-49-12-90-32-39-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

2) iwconfig output

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"lisleprivatesecurity"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:E7:0E:B9
          Bit Rate=54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=47/100  Signal level:-72 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



Regards,
Ramesh.

---

### Post by superprash2003 on 2009-01-07
your eth0 isnt getting an ip.. even after you disconnect LAN cable.. its ok even if eth0 has an ip as it would use the wlan0 interface that time.. to make sure.. once you disconnect the LAN cable and use wireles.. type route -n in your terminal

---

