---
title: "Wireless Atheros AR5007 (used on Acer Aspire 7720Z 5135)"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by danroonie on 2011-10-29
I've tried a bunch of solutions to try to get this wireless card to work on a clean install of 11.10 but no joy. Any ideas? I am willing to start from another clean install using my cat5 cable. 

Terminal: 


$ sudo modprob ath5k
sudo: modprob: command not found

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:4e:4a:ef  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe4e:4aef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10831190 (10.8 MB)  TX bytes:2555968 (2.5 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

