---
title: "Internet running very slowly - new computer added to household?"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by tegnoto89 on 2009-01-09
My computer's internet has been going very slowly lately, and it used to be so, so fast.  My sister just got her college laptop so now there's two computers using the wireless here... Could that be the issue?


If not, any suggestions?  Here's the info:

Ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1a:6b:38:aa:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5328 (5.3 KB)  TX bytes:5328 (5.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:76:8f:7f  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe76:8f7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5109586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6588502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2745235460 (2.7 GB)  TX bytes:3312703854 (3.3 GB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-76-8F-7F-66-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:80:A1:44   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-37 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by superprash2003 on 2009-01-09
try changing DNS servers to opendns - 208.67.222.222 and 208.67.220.220
Reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by tegnoto89 on 2009-01-09
Just a quick question on that - when adding the new line to the end, do I have to put a # before it?

---

### Post by superprash2003 on 2009-01-12
no.. do not put a #

---

