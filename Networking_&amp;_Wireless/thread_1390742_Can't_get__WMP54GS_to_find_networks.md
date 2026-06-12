---
title: "Can't get  WMP54GS to find networks"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by SCTPenguin on 2010-01-26
I just installed ubuntu and my wireless card WMP54GS doesn't seem to pick up any networks. I'm guessing I need the drivers, but after a few hours of google, I just can't seem to find the answer, or understand the answer. 

What driver do I need, and how can I install it. Thanks in advance.

I tried following some tutorial but network admin wont let me select the wireless connections to change the properties. Not sure what to do now. 

Here's what I get with wiconfig and ifconfig

```
collin@collin-ubuntu:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

collin@collin-ubuntu:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:23:0c:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

---

