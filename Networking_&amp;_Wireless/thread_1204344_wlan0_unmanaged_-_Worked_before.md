---
title: "wlan0 unmanaged - Worked before"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by ericmiller on 2009-07-04
Hello all -

I'm new here and new-ish to Linux. I installed Kubuntu 9.04 yesterday afternoon. My wireless card was detected just fine and worked completely all last night. This morning it no longer worked. the wlan0 interface is "unmanged." I can connect fine through eth0.

Can anybody help me understand what I need to do?

---

### Post by computer13137 on 2009-07-04
I've encountered this problem from time to time on my eeePC... but a quick reboot always fixed it.  I'd suggest you start there.

Cheers,
Kirk

---

### Post by ericmiller on 2009-07-04
I've already done so. 

Now I don't even have a wlan0.

eth0      Link encap:Ethernet  HWaddr 00:21:70:ae:6d:b8  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:feae:6db8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:12703311 (12.7 MB)  TX bytes:2088750 (2.0 MB)
          Memory:f6fe0000-f7000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41796 (41.7 KB)  TX bytes:41796 (41.7 KB)

pan0      Link encap:Ethernet  HWaddr 06:b9:47:d0:7e:4e  
          inet6 addr: fe80::4b9:47ff:fed0:7e4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:9387 (9.3 KB)

pan0:avahi Link encap:Ethernet  HWaddr 06:b9:47:d0:7e:4e  
          inet addr:169.254.7.54  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by Iowan on 2009-07-04
Post results of **lshw -C network** (entered in a terminal).

---

