---
title: "Intel PRO/Wireless 3945ABG stopped working from 7.10 on"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by chotteadore on 2009-07-16
Hi all,

I'm still stacked using ubuntu 7.04 (unsupported now) as it is the last version that allows me to use my Intel PRO/Wireless 3945ABG card. It should be a supported card, though.

I also have a built-in Ralink RT2561/RT61 rev B 802.11g in my laptop, which does not work and is off. Is it possible there is some kind of collision?

ubuntu 7.04 detects the wifi card automatically, however when I tried upgrading to every further version, I have no wireless connection. Network Manager shows both wireless cards, but says 'Inactive' state, in grey letters, so I cannot even try to customize.

When I run ubuntu 9.04 in live cd, ifconfig/iwconfig show:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:3d:f6:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:662675 (662.6 KB)  TX bytes:110428 (110.4 KB)
          Interrupt:16 Base address: 0x2000 

lo        Link encap:Local loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Alcance:Anfitrión
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13700 (13.7 KB)  TX bytes:13700 (13.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:80:5a:51:2d:76  
          inet6 addr: fe80::280:5aff:fe51:2d76/64 Alcance:Vínculo
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91365 (91.3 KB)  TX bytes:780 (780.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-80-5A-51-2D-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Radiolitec"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0A:78:89:B1:07   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=69/100  Signal level:-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


The ifconfig/iwconfig result in 7.04 version, which works:

user@pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:3D:F6:A4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:80:5A:51:2D:76  
          inet addr:192.168.0.13  Broadcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:5aff:fe51:2d76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9022 (8.8 KB)  TX bytes:5802 (5.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-80-5A-51-2D-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

user@pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Radiolitec"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0A:78:89:B1:07   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any hints? Thank you very much,

---

