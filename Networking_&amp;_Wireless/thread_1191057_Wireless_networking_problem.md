---
title: "Wireless networking problem"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by slow-wave on 2009-06-18
I'm using xubuntu 9.04 and I can't connect to my wireless network. It works perfectly fine wired. Been trying to solve this problem for hours but with no success.

I have no idea what's wrong. The networkmanager finds the wireless networks and such but when I try to connect to them it keeps on trying to connect for a while and then prompts me to enter the WEP-passphrase again as if I had entered the wrong one (which isn't the case, I'm positive). 

Here's my ifconfig and iwconfig output if that's any help

```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:69:7e:a4  
          inet addr:192.168.0.164  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe69:7ea4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4855727 (4.8 MB)  TX bytes:632043 (632.0 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5880 (5.8 KB)  TX bytes:5880 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:3d:ae:5a:eb  
          inet6 addr: fe80::20f:3dff:feae:5aeb/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7416 (7.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-3D-AE-5A-EB-61-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```


So what am I supposed to do there? What does all of this mean? I don't really have any proper experience working with this OS.

---

