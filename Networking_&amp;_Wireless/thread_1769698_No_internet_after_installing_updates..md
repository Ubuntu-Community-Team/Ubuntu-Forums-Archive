---
title: "No internet after installing updates."
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by omas_uk on 2011-05-28
Hello guys. I've got a problem after installing updates last week. Can't connect my laptop to internet - it keep saying Acquiring IP addressfollowed by timeout. I tried using Network Manager and now installed Wicd without any effect. I even updated system 9.04->10.4.1 and it didn't helped at all. Windows as well as ubuntu on my desktop can connect to internet without any problem. Unsecuring network doesn't help.

```
weronisia85@weronisia85-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:ba:f2:f3:9c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36705 (36.7 KB)  TX bytes:36705 (36.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:f0:82:75  
          inet6 addr: fe80::224:2bff:fef0:8275/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:326446 (326.4 KB)  TX bytes:274984 (274.9 KB)
``````
weronisia85@weronisia85-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub2-TWTJ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:04:C1:60:5A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

