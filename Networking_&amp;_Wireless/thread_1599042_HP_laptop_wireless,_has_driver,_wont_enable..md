---
title: "HP laptop wireless, has driver, wont enable."
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Baneblade on 2010-10-17
Iv just installed 10.10 but my wireless doesnt seem to be working.
The hardware and driver are both detected as the output from lshw shows ```
*-network DISABLED
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 61
                serial: 00:21:5c:0c:99:df
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=228.61.2.24 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:47 memory:f4300000-f4301fff
```
Iv checked that the physical switch is on at boot (since that used to be a problem with previous releases) but to no avail.

Help please? :/

---

### Post by Baneblade on 2010-10-17
I should probably mention that iv checked the wireless troubleshooting guide already, and after reaching the lshw stage it said to post here and ask in the irc support channel.

---

### Post by relay_man on 2010-10-17
Could you post the output of "ifconfig" (no quotes) from terminal?

---

### Post by Baneblade on 2010-10-17
> **relay_man said:**
> Could you post the output of "ifconfig" (no quotes) from terminal?

Sure
```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:69:af:84  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe69:af84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:327033134 (327.0 MB)  TX bytes:7563483 (7.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13040 (13.0 KB)  TX bytes:13040 (13.0 KB)

```

Since my wireless card can't be enabled I guess that is why it isn't showing up?

---

