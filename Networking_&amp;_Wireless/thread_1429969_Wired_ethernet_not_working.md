---
title: "Wired ethernet not working"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by wilee-nilee on 2010-03-14
I have a acer aspire one D250. The wireless is working but I have lost the hard plug. The router ethernet cord is work on another computer. This computer has XP/W7/Lucid running and I am unable to get plugged in access with any of the other the disto's or live CD's. There is a bios update available for this unit, I am not sure if this may fix this. there are no adjustments available in bios now for anything seemingly associated.

sudo lshw -C network 
  *-network               
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:24:2c:05:14:24 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k ip=192.168.0.68 latency=0 multicast=yes wireless=IEEE 802.11bg 
       resources: irq:16 memory:95000000-9500ffff 

 ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:05:14:24  
          inet addr:192.168.0.68  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::224:2cff:fe05:1424/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:4110 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3481 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:4446834 (4.4 MB)  TX bytes:344626 (344.6 KB) 

ifconfig lo 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB

---

### Post by wilee-nilee on 2010-03-15
Flashing the bios fixed the problem but created others in that I had set the XP/W7/Lucid as IDE. I got the Lucid back but couldn't fix the MS, no loss I just reinstalled.

---

