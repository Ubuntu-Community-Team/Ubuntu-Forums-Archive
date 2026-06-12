---
title: "Wifi connects but not working on hotspots"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by dhabsot on 2012-12-04
Hi all,

I have a Toshiba Satellite L855-10W and since I installed Kubuntu 12.04  the wifi connection doesn't work with the hotspot of my university (with Ubuntu 12.04/Linux Mint 14 it  works) but with home networks everything works fine.

The network has no protection because it allows you to surf the network with a login page or using a vpn.
When I try to load, for example, [www.google.com]("http://www.google.com") it should redirect me to the login page but it doesn't.
If I load gateway.wireless-campus.it (which is the link of the login page) the page loads well and it allows me to do the login, but even with the login done, i can't surf the internet.

Here is the output of ifconfig:
```
emanuele@emanuele-Kubuntu:~$ ifconfig
lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:36243 (36.2 KB)  Byte TX:36243 (36.2 KB)

wlan0     Link encap:Ethernet  HWaddr 24:ec:99:12:c3:90  
          indirizzo inet:10.83.60.60  Bcast:10.83.60.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::26ec:99ff:fe12:c390/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1598 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:63645 (63.6 KB)  Byte TX:183426 (183.4 KB)
```output of 'ping 10.83.60.60' which is the address of the gateway
```
emanuele@emanuele-Kubuntu:~$ ping 10.83.60.60
PING 10.83.60.60 (10.83.60.60) 56(84) bytes of data.
64 bytes from 10.83.60.60: icmp_req=1 ttl=64 time=0.044 ms
64 bytes from 10.83.60.60: icmp_req=2 ttl=64 time=0.033 ms
64 bytes from 10.83.60.60: icmp_req=3 ttl=64 time=0.034 ms
64 bytes from 10.83.60.60: icmp_req=4 ttl=64 time=0.038 ms
64 bytes from 10.83.60.60: icmp_req=5 ttl=64 time=0.040 ms
64 bytes from 10.83.60.60: icmp_req=6 ttl=64 time=0.038 ms
64 bytes from 10.83.60.60: icmp_req=7 ttl=64 time=0.040 ms
64 bytes from 10.83.60.60: icmp_req=8 ttl=64 time=0.037 ms
^C
--- 10.83.60.60 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6997ms
rtt min/avg/max/mdev = 0.033/0.038/0.044/0.003 ms
```Output of iwconfig
```
emanuele@emanuele-Kubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"UWiC-TridenteBraccio1d"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:E4:E4:E3:AF   
          Bit Rate=36 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0
```I already tried to look up for other threads but nothing worked... Hope you can help me! Thanks in advance! :)

P.S. I'm using this university network right now with Windows and Android (on my LG P500) and it works perfectly...

---

