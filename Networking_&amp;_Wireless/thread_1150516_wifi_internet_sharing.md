---
title: "wifi internet sharing"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2009-05-06
hi.
I use an internet connection on my ethernet interface and i want to share internet access on it through my wifi interface.
I was previously using Mandriva '08 and was able to do it by following these steps :-

1)[root@192 wolverine]# ifdown wlan0
2)[root@192 wolverine]# iwconfig wlan0 mode ad-hoc
3)[root@192 wolverine]# iwconfig wlan0 channel 11
4)[root@192 wolverine]# iwconfig wlan0 essid 'udis_wlan'
5)[root@192 wolverine]# iwconfig wlan0 key 1234567890
6)[root@192 wolverine]#
7)[root@192 wolverine]# ifconfig wlan0 up
8)[root@192 wolverine]# ifconfig wlan0 192.168.0.1
9)[root@192 wolverine]# iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.2 -j MASQUERADE


In Ubuntu 8.10:-
1)The command "ifdown wlan0" shows up "ifdown: interface wlan0 not configured"
before and after following the steps from 2 to 5
2)The fourth command sometimes shows some ip/op error
3)After these steps the a form comes up again and again asking me the key for the network but never connects.
4)If i create an access point using the network manager then i can connect to other computers on the network but i cannot ping them(strange!!)
5)ifup also shows an error -
Ignoring unknown interface wlan0=wlan0.

This is the line in the 'lspci' output - 

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)



My 'ifconfig' output is:-

root@nagraaj-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:17:bd:c2  
          inet addr:172.160.10.213  Bcast:172.160.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe17:bdc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19530015 (19.5 MB)  TX bytes:15298978 (15.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:548 (548.0 B)  TX bytes:548 (548.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d0:5a:7f  
          inet6 addr: fe80::218:deff:fed0:5a7f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9216 (9.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D0-5A-7F-61-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


and my 'iwconfig' output is:-

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.462 GHz  Cell: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


pleeeeeease help me.

---

