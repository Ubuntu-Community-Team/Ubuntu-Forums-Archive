---
title: "Wireless bridge and ping issues"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by k3pp0 on 2009-02-11
I have configured my desktop (ubuntu linux intrepid) with lan connection to internet (and dhcp server on lan), and a wifi card to act as an AP.

The idea is to connect my alix board with openwrt to the desktop AP, and exit to internet through it.

To do so, i bridged wifi and ethernet connection on the desktop, assigned a static ip to the wifi card (eg 192.168.2.1).

I manually set ip also on the alix board (eg 192.168.2.23)

I succesfully connect via wifi to the AP, but no ping is possible.

A look with wireshark shows ARP request from alix get no response.

Maybe it is due to a misconfiguration of the bridge on the ubuntu box but i am not finding any solution...if anybody could help..i owe you a beer :)

brctl show
```
bridge name	bridge id		STP enabled	interfaces
br0		8000.000b6b348894	no		ath0
							eth0

```

ifconfig
```
ath0      Link encap:Ethernet  HWaddr 00:0b:6b:34:88:94  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6bff:fe34:8894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5465 errors:0 dropped:10 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:150979 (150.9 KB)  TX bytes:6183633 (6.1 MB)

br0       Link encap:Ethernet  HWaddr 00:0b:6b:34:88:94  
          inet addr:10.210.63.82  Bcast:10.210.63.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:6bff:fe34:8894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4008208 (4.0 MB)  TX bytes:1241314 (1.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:e0:18:fd:84:e3  
          inet6 addr: fe80::2e0:18ff:fefd:84e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6852669 (6.8 MB)  TX bytes:2188516 (2.1 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25877 (25.8 KB)  TX bytes:25877 (25.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0B-6B-34-88-94-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26866 errors:0 dropped:0 overruns:0 frame:499865
          TX packets:12954 errors:1189 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1618234 (1.6 MB)  TX bytes:7188194 (7.1 MB)
          Interrupt:20
``` 

iwconfig

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

pan0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"k3pp0net"  Nickname:""
          Mode:Master  Frequency:2.417 GHz  Access Point: 00:0B:6B:34:88:94   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/70  Signal level=-75 dBm  Noise level=-96 dBm
          Rx invalid nwid:16539  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

```

---

### Post by superprash2003 on 2009-02-11
could be iptables blocking something.. post output of sudo iptables -L

---

### Post by k3pp0 on 2009-02-11
problem solved, seem it was a problem on the wireless client misconfigured, now all works like a charm.

Thanks anyway :)

---

