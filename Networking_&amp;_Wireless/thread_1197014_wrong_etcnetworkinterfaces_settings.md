---
title: "wrong /etc/network/interfaces settings"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by triangleSLO on 2009-06-25
I use Ubuntu 9.04 and i dual boot/winblows.

I use wireless connection (that works :) ) but if i type ifconfig command i get

```

eth0      Link encap:Ethernet  HWaddr   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

[B]eth1      Link encap:Ethernet  HWaddr 
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:feaf:4d08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38760 errors:0 dropped:0 overruns:0 frame:71
          TX packets:29661 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49003983 (49.0 MB)  TX bytes:4719745 (4.7 MB)
          Interrupt:16 Base address:0xc000 [/B]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

As you can see it looks like i am connected through eth1 and there is no wlan0 interface anywhere. I use **0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)**

These are my interfaces settings 
```

auto lo 
iface lo inet loopback

```

I dont know if winblows mixed up my settings, but i never had problems when i only had Ubuntu installed.

---

### Post by pytheas22 on 2009-06-25
While most wireless interfaces in Ubuntu are named wlan*, there's a Broadcom driver named 'wl' that assigns eth* names to the interfaces instead.  This may be what's going on in your case.  It's also possible that the system has just become confused for some reason about the aliases for the interface names.

So really this is nothing to worry about--eth1 is a wireless interface, and should be working fine for you.  It's perfectly fine to have a wireless interface named eth1, or anything else; wlan0 is just a convention.

---

