---
title: "trying to get wireless card to work (help me please)"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by rhythmiccycle on 2009-04-25
i've been following the steps on this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

when i type "  ndiswrapper -l" is says

> 
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)




then i type 

```

sudo depmod -a
  sudo modprobe ndiswrapper
tail /var/log/messages

```

and it says

```

Apr 25 12:00:41 ubuntu kernel: [   36.079840] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 25 12:00:44 ubuntu kernel: [   38.816208] b44: eth0: Link is up at 100 Mbps, full duplex.
Apr 25 12:00:44 ubuntu kernel: [   38.816215] b44: eth0: Flow control is off for TX and off for RX.
Apr 25 12:00:44 ubuntu kernel: [   39.042123] NET: Registered protocol family 17
Apr 25 12:00:50 ubuntu kernel: [   44.780257] NET: Registered protocol family 10
Apr 25 12:00:50 ubuntu kernel: [   44.781295] lo: Disabled Privacy Extensions
Apr 25 12:01:01 ubuntu pulseaudio[5263]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 25 12:01:01 ubuntu pulseaudio[5265]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 25 12:01:01 ubuntu pulseaudio[5265]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 25 12:20:33 ubuntu -- MARK --


```

also when I type "ifconfig"
it says
```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:66:67:c4  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe66:67c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:461463 (461.4 KB)  TX bytes:86653 (86.6 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

```


when I type "iwconfig"
it says
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```



so I tried the command line method to configure:

i type 
```
 
sudo ifdown wlan0

```
and it says
```
 
ifdown: interface wlan0 not configured

```

i also tryed

```

sudo ifdown eth0

```
and it says
```

Ignoring unknown interface eth0=eth0.

```

WHAT DO I DO?????
please help

---

### Post by rhythmiccycle on 2009-04-26
please help, i'm still stuck

---

