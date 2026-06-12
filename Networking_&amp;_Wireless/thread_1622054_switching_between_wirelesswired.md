---
title: "switching between wireless/wired"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by sr_guy on 2010-11-15
I have a single pc with both a wired and wireless card in it. I want to take down the wired connection down and bring the wireless connection up with a cronjob at certain parts of the day.

Here are my interfaces:

```

eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe64:ecfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:70751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15159563 (15.1 MB)  TX bytes:155842598 (155.8 MB)
          Interrupt:25 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5096 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13654287 (13.6 MB)  TX bytes:13654287 (13.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx
          inet6 addr: fe80::20f:3dff:fe85:4a9d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:37077 (37.0 KB)  TX bytes:58931 (58.9 KB)


```

If I try:

ifup wlan0

I get this error:
Ignoring unknown interface wlan0=wlan0.

Same error applies if eth0 is down and I try to bring it up, I get the same error. Am I missing something?


As a side note, here is my networking hardware:

```

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

---

### Post by grahammechanical on 2010-11-15
I have a ifconfig listing just like yours, where eth1 (in my case) is listed as UP and RUNNING and wlan0 is just listed as UP. I too tried, as an experiment, ifup wlan0 and I got the same result as you. Is it not possible to have two networks devices RUNNING at the same time? Yes. I have just tried using network manager to select my wireless network from those available and now I am connected by both eth1 and wlan0 and ifconfig shows both as UP and RUNNING. 

This does not help you much as you want to use a script to bring this about but it does show that it is possible.  Keep trying.

Regards.

---

### Post by grahammechanical on 2010-11-15
I was doing some research trying to find an answer to someone else's problem when I saw something that gave me an idea. The command ifup wlan0 might not work because wlan0 is already UP. What if you tried ifdown wlan0 and then ifup wlan0? Would this work? I have no idea. It just might.

Regards.

---

### Post by LeMeun on 2010-11-15
try sudo ifconfig wlan0 down instead of ifup wlan

---

