---
title: "wireless keeps disconnecting and connecting"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by senca on 2011-02-15
hey,
I just bought a new laptop. This one came with win7 home. The wireless works perfect. Today I installed ubuntu 10.4 next to windows. I made a first connection which went easy. But after 30 seconds it disconnects. Then it tries 30 seconds to reconnect. It reconnects and after 30 secodns or so, it disconnects again. It keeps doing this all the time on ubuntu while on windows it works without any problems. 
This is what sais under the device manager for my wirelesscard stuff:

Intel(R) WiFi 1000 BGN
Microsoft Virtual WiFi Miniport Adapter #2
Microsoft Virtual WiFi Miniport Adapter
Realtek PCIe GBE Family Controller

Does anyone have any idea what the problem could be? Updating is not possible because the connection keeps disconnecting all the time. (the laptop is a Dell XPS)

edit: I have a wireless router form our provider but have another wireless D-link router connected to the first one to improve the signal
also pasted an ifconfig from ubuntu:

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:6b:fe:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11608 (11.6 KB)  TX bytes:11608 (11.6 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:0c:47:7c  
          inet6 addr: fe80::8ea9:82ff:fe0c:477c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12934230 (12.9 MB)  TX bytes:436780 (436.7 KB)

---

### Post by senca on 2011-03-01
I removed windows, started with a clean ubuntu setup and the problems were gone.
Guess dual booting just doesn't work properly, especially on a Dell

---

