---
title: "Installed USB Wireless, Internal Network Card Not Working"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by grejanter on 2011-04-20
Installed a Wireless USB Card to use with Aircrack-ng, it is using RTL8187 Driver, and my internal card was using  wl driver, the card is BCM4313 14E:4727...

Here is my ifconfig and iwconfig, my eth0 only shows in ifconfig, not in iwconfig...
Wlan0 is the USB Wireless.. I am on a Dell Inspiron 15R.

Ifconfig:
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:a2:3a:e1  
          inet addr:127.0.0.1  Bcast:127.255.255.255  Mask:255.0.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12272 (12.2 KB)  TX bytes:12272 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 38:0a:0a:b0:30:c7  
          inet addr:128.235.70.98  Bcast:128.235.79.255  Mask:255.255.240.0
          inet6 addr: fe80::3a0a:aff:feb0:30c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9467130 (9.4 MB)  TX bytes:745612 (745.6 KB)


iwconfig : lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"njit"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:40:96:53:44:F5   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

