---
title: "[Jaunty] Wifi (Broadcom) stuck at ~1mb/s."
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by fluffystaxx on 2009-08-25
Hey there, I have a little problem I havent been able to solve yet, and I dont really know the cause either. It occured ~3 weeks ago, a fresh install doenst cure it either.

My WiFi is stuck at around 1mbit (100kbps down) and a ping of 36ms. Normally I am able to leech out up to 16mbit down with a ping of 30ms. 

The problem is similar to this thread,
[http://ubuntuforums.org/showthread.php?t=1227509&highlight=pernicious](http://ubuntuforums.org/showthread.php?t=1227509&highlight=pernicious)
But the described fix: "iwconfig wlan0 rate 54M" Does not solve the problem. It did however work once. It does not work when its fixed either.

I read something about a HAL update somewhere, but I dont wheter this is the problem or not. Newly installed system is fully updated, problem did not seem to occur before updates. (So i might roll back all updates and install them one by one, but that isnt a fix).

---------------
Background information

lspci | grep Broadcom
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"WIFIHUB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:54:74:30:FA   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=88/100  Signal level:-45 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

``````

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:56:ce:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:50:35:59  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe50:3559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:278126152 (278.1 MB)  TX bytes:25383425 (25.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-50-35-59-35-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

