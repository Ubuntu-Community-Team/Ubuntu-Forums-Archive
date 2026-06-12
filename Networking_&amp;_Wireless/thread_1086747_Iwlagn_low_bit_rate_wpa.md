---
title: "Iwlagn low bit rate wpa"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Jamez0905 on 2009-03-04
I recently reinstalled ubuntu 8.10 and ever since I only get 1M - 2M bit rate while I'm at my home using wpa2 encryption on the iwlagn driver.  It works fine on open and wep encryptions but I am not going to sacrifice security for speed.  This had started on my previous installation too after an update, because before then it worked fine, but now I am stuck at a very low bit rate which is essentially unusable, I will post any info that you guys ask for but I don't know what you would need.

The connection starts out at 54M when it first connects but then quickly deteriorates to 1M

Also I tried compiling a kernel (2.6.28-something) and it worked just fine again, but there were many other errors during compiling which made it not a good choice to use.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:3f:7c:9d  
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
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53330 (53.3 KB)  TX bytes:53330 (53.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:73:92:c0  
          inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe73:92c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20069090 (20.0 MB)  TX bytes:11373275 (11.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-EA-73-92-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Witt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:78:FA:FA   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/100  Signal level:-59 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

---

### Post by Jamez0905 on 2009-03-04
Anybody?

---

