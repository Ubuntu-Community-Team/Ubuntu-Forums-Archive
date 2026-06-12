---
title: "What could be causing my slow wireless connection?"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Dr.Suave on 2009-02-17
Hi there - After installing Intrepid Ibex on a computer using a RaLink RT2500 802.11g Cardbus/mini-PCI, I found my internet connection was ridiculously slow - maximum speed about 20 kb/s - I should have been hitting at least 150 kb/s.

I found that part of the cause was that the iwconfig bit rate was set to 1 mb/s - I've now set it to 54 mb/s - but I'm still only hitting 60 kb/s download speed!

I've disable ipv6, enabled openDNS, made sure my MTU values were right (I think they are) and still can't get my proper speed. I may have made a pretty basic mistake (I'm not even sure if 54M was the right bit rate to set iwconfig to), so don't think anything is too obvious to point out...

here are the results of the iwconfig command:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"LindaHome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6D:52:F6   
          Bit Rate=54 Mb/s   Tx-Power=26 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=64/100  Signal level:-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

and the ifconfig command:

```
eth0      Link encap:Ethernet  HWaddr 00:18:f3:78:ef:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:f2:b9:39  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56630196 (56.6 MB)  TX bytes:6516975 (6.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-F2-B9-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
If anyone wants to see any other commands please let me know! This internet speed is driving me mad!

Thanks for reading,

Wilf

---

### Post by Dr.Suave on 2009-02-18
Bump!

---

### Post by RavanH on 2009-07-12
Old post but if still relevant (still using ralink) please check out my fix on [http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785) which involves switching to Wicd plus a small pre-connection script.

Let me know if it works or not :)

---

