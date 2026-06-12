---
title: "Can't connect to Internet via WiFi"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by andyscrol on 2010-09-14
Hello!
I'm trying to set up Internet connection via WiFi (have ADSL modem with WiFi) but unsuccessful. I can see Wireless Networks available but can't establish encrypted connection with specific one (assigned by provider).

Here's what I have if this may help:
> alexey@alexey-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:82:c7:75  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe82:c775/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6970429 (6.9 MB)  TX bytes:1441288 (1.4 MB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:430020 (430.0 KB)  TX bytes:430020 (430.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:178.122.72.222  P-t-P:82.209.195.83  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:6585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:5627727 (5.6 MB)  TX bytes:1050063 (1.0 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:5d:b3:e6  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fe5d:b3e6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have to assign eth0 & wlan0 inet addr. manually every time (can I set it up just once and for all?) - it's a SIDE question
Also 
>  wlan0     IEEE 802.11abgn  ESSID:"<ZTE>"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


---

