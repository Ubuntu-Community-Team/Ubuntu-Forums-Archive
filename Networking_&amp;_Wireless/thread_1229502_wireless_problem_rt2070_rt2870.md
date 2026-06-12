---
title: "wireless problem rt2070 rt2870"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by riccardoced on 2009-08-02
Hi all
I managed to install a ralink 2070 wireless usb by adding the usb ID to the rt2870 file .
I does recognize the device ,it flashes as it should but I can't scan or connect at all.
network manager and Rutilit Network manager both list it as disconnected.
This is output of ifconfig ra0       Link encap:Ethernet  HWaddr 00:08:10:72:07:99  
          inet6 addr: fe80::208:10ff:fe72:799/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:59024 (59.0 KB)
this is output of iwconfig ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Also how do i set managed mode and how do i set access point association? what about open ssid?
I appreciate any help
thanks

---

