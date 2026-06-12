---
title: "Wireless suddenly stopped working"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by me97esn on 2010-01-07
This morning I could use Wireless network. I could see several different networks in my range. Then suddenly the network stopped working, and I can no longer see any networks under "Wireless networks".
The Wired networks works fine.

I tried upgrading ubuntu, but nothing changed. Just to confirm, I rebooted the computer in Windows Vista (Dual boot) and confirmed that Wireless worked fine there. No hardware problem then.

The suggestions I have found on this and other forums suggest looking at the output from iwconfig and ifconfig. 
But since I'm a n00b at Ubuntu I don't know what to make of it.

This is the output:
emil@emils:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"(-C-)"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

emil@emils:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:29:7a:de:98  
          inet addr:10.110.171.134  Bcast:10.110.171.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:29ff:fe7a:de98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5696435 (5.6 MB)  TX bytes:874450 (874.4 KB)
          Memory:e8020000-e8040000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:93:d7:71  
          inet6 addr: fe80::21f:3bff:fe93:d771/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:576 (576.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-93-D7-71-39-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

emil@emils:~$

---

### Post by puppywhacker on 2010-01-07
your wireless connection is "Not-Associated" with your accesspoint you can use
```
sudo iwconfig wlan0 ap 00:13:D3:6F:92:99
```

To find the correct accesspoint name you can scan with
```
iwlist wlan0 scan
```

---

