---
title: "Slow wireless internet, large invalid misc numbers"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by Delodic on 2011-11-03
Hey all!

For some while now I've been using Ubuntu without any problems. However, a couple of weeks ago I started having trouble with my wireless connection. Once I connect, everything is fine and I can reach normal speeds. But after a while it drops back and I reach 100 kb/s at most. If I disconnect and reconnect the speed is fine again for a short while. 

iwconfig shows large numbers of excessive retries and invalid misc. So I suppose it's a driver problem? When I boot on windows I have absolutely no problems with the wireless connection. 

I've trouble finding the solution online and it doesn't really help that my connection speed sucks as well at the moment.

iwconfig shows:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Batcave"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:11:50:1B:A0:0F   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:748  Invalid misc:6053   Missed beacon:0

```

lshw -C network:
```

WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:09:40:f0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 multicast=yes port=twisted pair
       resources: irq:45 memory:fe9c0000-fe9fffff ioport:cc00(size=128)
  *-network
       description: Wireless interface
       product: RT2500 802.11g
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 01
       serial: 00:0c:f6:18:a1:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=3.0.0-12-generic firmware=N/A ip=192.168.2.5 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:febfe000-febfffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by distobj on 2011-12-13
Did you manage to resolve your problem?  The same symptoms have started on my Oneiric/64 laptop sometime over the past 2-3 days;

Tx excessive retries:3242  Invalid misc:1308   Missed beacon:0

Retries increase by 1 every second or so.

---

