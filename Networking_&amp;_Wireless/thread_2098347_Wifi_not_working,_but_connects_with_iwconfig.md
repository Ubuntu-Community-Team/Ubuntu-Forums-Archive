---
title: "Wifi not working, but connects with iwconfig"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by jpmaglutac on 2012-12-26
So I just got a new USB wireless adapter and it didn't seem to be working out of the box. Did a bit of tinkering and I got it to show up on iwconfig and was able to successfully connect it using iwconfig. Problem is, the internet isn't working at all.

The wireless options do not appear on KNetworkManager at all, but the device is appearing just fine under the Device Viewer of KInfoCenter 

Command line results:
lsusb:
```
Bus 001 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
```

iwconfig:
```
ra0       Ralink STA  ESSID:"TP-LINK"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1D:0F:E5:46:14   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=73/100  Signal level:-69 dBm  Noise level:-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig:
```
ra0       Link encap:Ethernet  HWaddr 00:13:3f:00:20:42  
          inet addr:192.168.1.109  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:487489 (487.4 KB)  TX bytes:12046 (12.0 KB)

```

lshw -C network:
```
*-network:1
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:13:3f:00:20:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=192.168.1.109 multicast=yes wireless=Ralink STA
```
pinging my gateway works, and pinging 8.8.8.8 works as well. I'm thinking this might be a DNS problem

Any help would be greatly appreciated!

---

### Post by jpmaglutac on 2012-12-26
Okay so I don't know if installing wicd made it work or if adding "dns-nameservers 8.8.8.8" to /etc/network/interfaces made it work....



Either way, it is working, and I will keep my solution here for posterity

---

