---
title: "Atheros and lags in games"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Majki-Fajki on 2012-02-20
I have a problem with networking for some time. About half year ago, my  AR542x Wireless Card started to make some trouble. It lags from time to time. In games it shows as massive lag in almost regular intervals. Approximately 45 - 60 seconds and it last for about 4 - 5 seconds. After that, everything is back to normal.

So. My hardware:
```
michal@michal-F5N:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
```Or simply Asus F5N laptop.

I would be very happy to provide additional logs and configs, just tell me what to do.

I have done some ping tests. When it was run with eth0 connection, everything was fine.

```
--- google.pl ping statistics ---
115 packets transmitted, 115 received, 0% packet loss, time 114156ms
rtt min/avg/max/mdev = 54.541/58.714/147.760/8.882 ms
```But with ath0, we have some interesting results.

```
michal@michal-F5N:~$ ping google.pl
PING google.pl (173.194.69.94) 56(84) bytes of data.
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=1 ttl=48 time=62.1 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=2 ttl=48 time=56.3 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=3 ttl=48 time=61.5 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=4 ttl=48 time=61.3 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=5 ttl=48 time=62.4 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=6 ttl=48 time=61.9 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=7 ttl=48 time=58.2 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=8 ttl=48 time=61.2 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=9 ttl=48 time=61.6 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=10 ttl=48 time=56.6 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=11 ttl=48 time=61.8 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=12 ttl=48 time=61.9 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=13 ttl=48 time=56.5 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=14 ttl=48 time=62.1 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=15 ttl=48 time=56.2 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=16 ttl=48 time=56.4 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=17 ttl=48 time=62.0 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=18 ttl=48 time=56.1 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=19 ttl=48 time=63.0 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=20 ttl=48 time=62.0 ms
**64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=21 ttl=48 time=169 ms**
**64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=22 ttl=48 time=287 ms**
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=23 ttl=48 time=62.7 ms
**64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=24 ttl=48 time=150 ms**
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=25 ttl=48 time=62.8 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=26 ttl=48 time=57.3 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=27 ttl=48 time=55.6 ms
64 bytes from bk-in-f94.1e100.net (173.194.69.94): icmp_req=28 ttl=48 time=61.6 ms
^C
--- google.pl ping statistics ---
28 packets transmitted, 28 received, 0% packet loss, time 27039ms
rtt min/avg/max/mdev = 55.684/75.392/287.995/48.470 ms
```

Notice lines I have marked with bold. Something very bad happens there. On Wired connection I had no such problems.

I have found this thread: 
[http://ubuntuforums.org/showthread.php?t=1316066&highlight=atheros+lags](http://ubuntuforums.org/showthread.php?t=1316066&highlight=atheros+lags)

Is ath5k driver really that poor?

I'm using Ubuntu 11.10, fully updated.

---

