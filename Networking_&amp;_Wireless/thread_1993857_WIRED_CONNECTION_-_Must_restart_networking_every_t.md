---
title: "WIRED CONNECTION - Must restart networking every two hours"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by jjmatt on 2012-06-02
Ok, so I've got an issue where in ubuntu 12.04 x64 every 30 minutes or so, (haven't actually timed it, just estimating) I have to restart my networking (NM Applet -> uncheck enable networking, then recheck) in order to get internet access again. My computer is wired directly to my verizon router, and I dual boot with windows 7, which has no issues like this, so it's got to be a software issue. Basically, I'll just be browsing the web, then all of the sudden the next page won't load for no reason, nm-applet says my wired connection is still active. Then I restart networking, and everything works fine again. I haven't tried this with my other ethernet port yet.

Here's some relevant information, let me know if there's anything else I can provide to help you help me :):

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr f4:6d:04:99:d8:33  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe99:d833/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69749 errors:0 dropped:1476 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163979038 (163.9 MB)  TX bytes:10534195 (10.5 MB)
          Interrupt:16 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr f4:6d:04:99:cf:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:fb600000-fb620000 
```

```
sudo lshw -class network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: f4:6d:04:99:cf:76
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:65 memory:fb600000-fb61ffff memory:fb628000-fb628fff ioport:f040(size=32)
  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: f4:6d:04:99:d8:33
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:c000(size=256) memory:fb221000-fb2210ff memory:fb200000-fb21ffff

```

---

### Post by jjmatt on 2012-06-04
Bump

---

