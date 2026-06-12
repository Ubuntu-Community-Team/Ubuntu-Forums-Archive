---
title: "Wireless Connected no internet though"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by jbutler8 on 2010-09-28
I am using Ubuntu 10.04 on a Dell XPS M1530.

The network I am trying to use, is wireless with mac address filtering.  I know my wireless card works, since I use it on the college wireless networks.  I can connect to the wireless but cannot access the internet via wifi.

Here is the output of ifconfig.  Note: The reason for the eth0 hardware address is the same is that I am currently using mac changer to set its mac address so I can use the internet. This also seems to imply that my mac address is input in the router correctly.


```
eth0      Link encap:Ethernet  HWaddr 00:1f:3b:7b:7e:45  
          inet addr:192.168.1.192  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe56:289b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2805188 (2.8 MB)  TX bytes:678268 (678.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76212 (76.2 KB)  TX bytes:76212 (76.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:7b:7e:45  
          inet6 addr: fe80::21f:3bff:fe7b:7e45/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76472 (76.4 KB)  TX bytes:3838 (3.8 KB)
```

output of iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"\x05\xEF\xF7\x00\xE9\xA1:\xE5\xCA
          \x0B\xCB\xD0HGd\xBD\x1F#\x1E\xA8\x1C{d\xC5\x14sZ\xC5^Kyc"  
          Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

---

