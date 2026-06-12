---
title: "Wireshark data"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by snowboardtux on 2010-04-29
First off hello everyone, new here and fairly new to Linux but have been creeping for awhile, and all your help is amazing, so glad I changed to Ubuntu (9.10) :)

Here's my problem. When I run wireshark, I cannot capture http packets when scanning my network on mon0, only if I put it on "Psuedo device that captures on all interfaces". I recently tried to change my mac address just to try something new, and I think something isn't right.

After I use 
```
sudo airmon-ng start wlan0
```> PID    Name
882    avahi-daemon
883    avahi-daemon
1338    NetworkManager
1437    wpa_supplicant
1834    dhclient
Process with PID 1834 (dhclient) is running on interface wlan0
Process with PID 7283 (dumpcap) is running on interface mon0
and then check my ifconfig..

> eth0      Link encap:Ethernet  HWaddr 00:26:22:73:78:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5763 (5.7 KB)  TX bytes:5763 (5.7 KB)

mon0      Link encap:UNSPEC  HWaddr 0C-EE-E6-C6-E5-A7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:71574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31291128 (31.2 MB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 0c:ee:e6:c6:e5:a7  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eee:e6ff:fec6:e5a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32896322 (32.8 MB)  TX bytes:4850739 (4.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 0C-EE-E6-C6-E5-A7-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**and my IW config..**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"2WIRE806"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:7C:27:B9:99   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11bgn  Mode:Monitor  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0I'm stumped. Before when wireshark was outputing the http data, the mon0 would show up below wlan0. Now it shows above. Obviously I messed something up here, lol. Hope to hear from someone that knows how to solve this, if you need any more data posted feel free to yell at me and let me know.

Thanks for your time!

---

### Post by snowboardtux on 2010-04-29
Bump

I used to capture on mon0, shouldn't it be shown in monitor mode?

---

### Post by snowboardtux on 2010-04-29
Ok quick update, my goal here is to enable mon0 so I can put it into Monitor Mode, which it is but says " Link encap:UNSPEC". I think this is the problem, but don't know where to go from here????

Already have tried putting wlan0 in monitor mode and I cannot, only can get it into managed mode, using compat-wireless drivers. Atheros card.

---

### Post by snowboardtux on 2010-04-29
Bump, anybody? :(

---

