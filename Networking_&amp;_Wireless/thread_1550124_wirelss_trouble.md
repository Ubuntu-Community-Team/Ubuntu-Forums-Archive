---
title: "wirelss trouble"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by valio0000 on 2010-08-10
Hello,

I've got problems with my WI-FI. The connection is established but i got no signal and cannot surf or ping annything.

Here is what i get when i type ifconfig:

valio0000@valio-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:aa:8e:b6  
          inet6 addr: fe80::20f:1fff:feaa:8eb6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:119715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168459405 (168.4 MB)  TX bytes:5722436 (5.7 MB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17069 (17.0 KB)  TX bytes:17069 (17.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:c3:e8:9d  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fec3:e89d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33884 (33.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-96-C3-E8-9D-63-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Here is what i get when i type iwconfig:

valio0000@valio-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"*****************"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 56:FF:2D:27:67:18   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


By typing ip route list:

valio0000@valio-laptop:~$ ip route list
10.42.43.0/24 dev wlan0  proto kernel  scope link  src 10.42.43.1  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 

Thank you for your reply

[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

