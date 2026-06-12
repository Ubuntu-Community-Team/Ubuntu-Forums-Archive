---
title: "Wireless Connection no internet (10.04)"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by 1eca on 2012-10-29
Hey, this has been an issue for a couple days now. My system connects to my network just fine, but doesn't want to connect to the internet. I have tried rebooting both my computer and my router to no avail (roommates are connected and online without issue). Also tried switching to a static IP which worked briefly and then stopped. Ifconfig reports:

```
eth0   Link encap:Ethernet. HWaddr 00:17:f2:27:9d:81
                      UP BROADCAST MULTICAST MTU:1500 Metric:1
                      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                      collisions:0 txqueuelen:1000
                      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
                      Interrupt:16

lo   Link encap:Local Loopback
      inet addr:127.0.0.1. Mask:255.0.0.0
      Inet6 addr:  : :1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436. Metric:1
      RX packets:3136 errors:0 dropped:0 overruns:0 frame:0
      TX packets:3136 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:249368 (249.3 KB)  TX bytes:249368 (249.3 KB)

wlan0  Link encap:Ethernet HWaddr 00:17:f2:42:54:7b
            inet addr:192.168.100.14 Bcast:192.168.100.255. Mask:255.255.255.0
            inet6 addr:  fe80: :217:f2ff:fe42:547b/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
            RX packets:519 errors:0 dropped:0 overruns:0 frame:0
            TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:105323 (105.3 KB)  TX bytes:85161 (85.1 KB)
```

All help with this is greatly appreciated, been trying to troubleshoot myself but just cannot figure out what is wrong.

---

