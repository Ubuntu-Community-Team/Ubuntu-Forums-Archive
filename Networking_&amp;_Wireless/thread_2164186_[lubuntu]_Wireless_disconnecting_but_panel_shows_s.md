---
title: "[lubuntu] Wireless disconnecting but panel shows still connected"
date: 2013-07-30
forum: Networking &amp; Wireless
---

### Post by beardedwondr on 2013-07-30
My wifi connection drops intermittently however the panel next to the clock shows that it's still connected. The only way to get it back is to click on my network from the panel drop-down.

Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

ifconfig:
```
wlan1     Link encap:Ethernet  HWaddr 00:18:39:11:bf:13  
          inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:39ff:fe11:bf13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2255183 errors:0 dropped:15 overruns:0 frame:0
          TX packets:2442251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
```

lspci -vv -s 02:00.0
```
02:00.0 Network controller: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] (rev 01)
    Subsystem: Linksys WPC300N v2 Wireless-N Notebook Adapter
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 30000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] #80 [0000]
    Kernel driver in use: ath9k
```

Is there anything I can do to find out what's causing the problem?

---

### Post by praseodym on 2013-07-31
Deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by beardedwondr on 2013-08-01
Thanks, I have doen that. I will see if the disconnecting problem continues.

---

