---
title: "What to do when wireless signal drops out?"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by Pipps on 2012-07-14
I have a small netbook with a Broadcom BCM4312 wireless card. I have the low power driver [installed]("http://ubuntuforums.org/showthread.php?p=12094085#post12094085"). It seems to have been working successfully at first.

The connection now seems to drop out after half an hour or so of usage. Sometimes a reboot resolves it. Sometimes not, and I have to connect the ethernet cable. The wireless does usually work if I leave the machine switched off and return to it later.

Are there any commands that I can run in the terminal to check what the problem might be when the wireless drops out like this please?

---

### Post by Pipps on 2012-07-14
It is only Ubuntu that drops-out on my network. All other connected computers are fine.

What could this be?

---

### Post by Kirk Schnable on 2012-07-15
When your connection isn't working, run:

```
ifconfig
```

```
iwconfig
```

That will tell us if you have an IP, and if you're associated with the access point. 

Kirk

---

### Post by Pipps on 2012-07-22
Hello, thanks for your help. Here is what those two commands have returned, in all cases:


**1. When the wireless connection seems to drop:**

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:f2:9e:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49282 (49.2 KB)  TX bytes:20608 (20.6 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24281 (24.2 KB)  TX bytes:24281 (24.2 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:6d:7d:73  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe6d:7d73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12361261 (12.3 MB)  TX bytes:744390 (744.3 KB)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"virginmedia542841"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:4E:7F:DF:41:D8   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:833   Missed beacon:0

eth0      no wireless extensions.

```


**2. When the wireless connection is working fine:**
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:f2:9e:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3855648 (3.8 MB)  TX bytes:475579 (475.5 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54062 (54.0 KB)  TX bytes:54062 (54.0 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:6d:7d:73  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe6d:7d73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165233 (165.2 KB)  TX bytes:65333 (65.3 KB)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"virginmedia542841"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:4E:7F:DF:41:D8   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-6 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

eth0      no wireless extensions.

```


**3. When the ethernet cable is connected and working fine:**
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:f2:9e:9a  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fef2:9e9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2971089 (2.9 MB)  TX bytes:360724 (360.7 KB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20795 (20.7 KB)  TX bytes:20795 (20.7 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:6d:7d:73  
          inet6 addr: fe80::721a:4ff:fe6d:7d73/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149447 (149.4 KB)  TX bytes:44601 (44.6 KB)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```


What could be the problem?

---

