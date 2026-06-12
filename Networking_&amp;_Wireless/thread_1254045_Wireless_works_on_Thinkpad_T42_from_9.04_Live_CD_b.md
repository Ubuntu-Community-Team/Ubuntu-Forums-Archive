---
title: "Wireless works on Thinkpad T42 from 9.04 Live CD but not after install"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by gregb11 on 2009-08-30
I have a Thinkpad T42 with Ubuntu 9.04 as the only OS.  Wireless worked fine from the Live CD but not after installation.  I have spent hours trying various fixes including ndiswrapper and WICD but without success.  By the way, WICD unistalled the Network Manager.  (However, as a newbie, perhaps I did not install those packages correctly.)  Does anyone have any suggestions what to do now?

Thanks
Greg

---

### Post by uylug on 2009-08-30
Sure. What is the ouput of 
```
ifconfig
```
```
iwconfig
```
```
ndiswrapper -l
```

---

### Post by gregb11 on 2009-08-31
> **uylug said:**
> Sure. What is the ouput of 
```
ifconfig
``````
iwconfig
``````
ndiswrapper -l
```

iconfig
eth0      Link encap:Ethernet  HWaddr 00:11:25:2b:c9:8b  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe2b:c98b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1690197 (1.6 MB)  TX bytes:470195 (470.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:56:80:63  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:c0210000-c0220000 


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net5211 : driver installed
    device (168C:0013) present (alternate driver: ath5k)

Thanks
Greg

---

