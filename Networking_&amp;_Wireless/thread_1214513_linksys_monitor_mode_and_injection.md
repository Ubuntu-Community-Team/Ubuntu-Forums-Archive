---
title: "linksys monitor mode and injection"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by the wombat on 2009-07-16
Hey there, 
   Ive been getting into trying to crack WEP/WPA keys and im having a little trouble with my wireless card. I have a linksys WMP54G v4.1 and i can only get it into monitor mode when wireless is shut off. Also, im pretty sure this card isnt capable of packet injection, or is it? do i need a patched driver, and if so where would i find one? If this has been posted already a link to that thread would be greatly appreciated. thanks!!

output of iwconfig:
```
nate@sam3:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:D7:1B:F4   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

and ifconfig
```
nate@sam3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:76:3d:75:2e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
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

wlan0     Link encap:Ethernet  HWaddr 00:1c:10:6e:95:ee  
          inet addr:192.168.254.3  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:10ff:fe6e:95ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31273 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33934515 (33.9 MB)  TX bytes:6335781 (6.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-10-6E-95-EE-35-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

