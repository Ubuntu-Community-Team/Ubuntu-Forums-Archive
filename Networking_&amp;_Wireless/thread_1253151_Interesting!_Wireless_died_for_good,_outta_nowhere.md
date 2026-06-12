---
title: "Interesting! Wireless died for good, outta nowhere!"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by Aped on 2009-08-29
Yeah! I don't know if any of the rest of you are in southern California at the moment, but mine is one of the homes about to burn, so we were evacuated. I snagged this laptop to use on the go until I had a chance to set up a more permanent system...

However! As I booted it up and started browsing on my own home network before packing it, the connection died. 

Didn't think much of it at the time, but now my wireless adapter doesn't even recognise networks, let alone connect to them. What could have happened?

Some relevant info:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:e2:71:95  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fee2:7195/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224452 (224.4 KB)  TX bytes:37606 (37.6 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:62:f4:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1496 (1.4 KB)  TX bytes:1496 (1.4 KB)

```

As you can see, wlan0 isn't even listed here. 

If you want anything else pasted in here, let me know. I'm really hoping that a modprobe XXX might fix this... could a driver be at fault even?

I don't want to believe that the hardware could have failed, though it's hard to imagine what else it could be under the circumstances.

---

### Post by Iowan on 2009-08-29
Check **lshw -C network**. That might let you identify your wireless device and see if (maybe?) it is associated with eth1 (my laptop does).

---

### Post by Aped on 2009-08-29
> **Iowan said:**
> Check **lshw -C network**. That might let you identify your wireless device and see if (maybe?) it is associated with eth1 (my laptop does).

Ahem: 

```

  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:e2:71:95
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.64 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:62:f4:7b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2e:36:60:70:67:e9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Even if it were set to eth1, I don't get why that would mean that my connection would suddenly disappear in the middle of a file transfer or whatever I was doing and then *never* work again.

---

### Post by Iowan on 2009-08-30
It would appear that your wireless is labeled **eth1**. The **ifconfig** you posted earlier shows eth0 with an IP address.  Network Manager only manages one interface at a time.  That doesn't explain why "my connection would suddenly disappear in the middle of a file transfer or whatever I was doing and then *never* work again."

---

