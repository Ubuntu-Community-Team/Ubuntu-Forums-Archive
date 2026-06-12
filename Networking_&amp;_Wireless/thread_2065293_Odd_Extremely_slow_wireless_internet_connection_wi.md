---
title: "Odd? Extremely slow wireless internet connection with Alcatel wireless router."
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by andey on 2012-10-01
Running Ubuntu 12.04, my internet at home works fine.
Just started working a new job (bring your own laptop), and my internet at the work place is EXTREMELY SLOW.

I checked ifconfig, and I get these new vmnet's?. I don't know what those are.

```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:5e:9e:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41253 (41.2 KB)  TX bytes:41253 (41.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.172.1  Bcast:172.16.172.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.46.1  Bcast:192.168.46.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:1f:af:bf  
          inet addr:192.168.2.53  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fe1f:afbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:241339 (241.3 KB)  TX bytes:103425 (103.4 KB)
```

[[IMG]http://img1.UploadScreenshot.com/images/main/10/27404405024.png[/IMG]](http://www.UploadScreenshot.com/image/1486132/1068446)

**They are using a "Alcatel Lucent 7130 5VzA2001" Router**
I have access to the config. 
Here are the [current settings](http://i.imgur.com/ofGu9.png).

[COLOR="Red"]However, when I run Windows 7, the internet works fine.[/COLOR]
[[IMG]http://www.speedtest.net/result/2214523817.png[/IMG]](http://www.speedtest.net)

On Ubuntu, I can't even completely load the speedtest.net website.

**Anyone have any idea what the problem is?**

---

