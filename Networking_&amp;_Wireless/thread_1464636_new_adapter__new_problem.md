---
title: "new adapter / new problem"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by arolfsen on 2010-04-28
I recently picked up a belkin f5d7050b

I know that It is working as the network icon in the applications bar at the top shows my network. for whatever reason I can't seem to connect to the network however. every time i click on it, it says network disconnected. thoughts?

---

### Post by Iowan on 2010-04-28
Post **ifconfig -a** and **sudo lshw -C network**

---

### Post by arolfsen on 2010-04-28
ifconfig -a:

eth0        Link encap:Ethernet HWaddr 00:0b:cd:a6:7c:77
            UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0(0.0b) TX bytes:0 (0.0b)
            interrupt:10 base address:0xa000

lo          Link encap:Local Loopback
            inet addr: 127.0.0.1 Mask:255.0.0.0
            inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX Packets:4 errors:0 dropped:0 overruns:0 frame:0
            TX Packets:4 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:240 (240.0b) TX bytes:240 (240.0b)

wlan3:      Link encap:ethernet HWaddr 00:22:75:4f:7e:97
            inet6 addr: fe80::222:75ff:fe4f:7e97/64 scope:Link
            UP BROADCAST MULTICAST MTU:1500 Metric:1
            RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX Packets:10 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0b) TX bytes:2016 (2.0kb)

wmaster0    Link encap:UNSPEC HWaddr:00-22-75-4f-7e-97-34-66-00-00-00-00-00-00-00-00
            UP RUNNING MTU:0 Metric:1
            RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX Bytes:0 (0.0b) TX bytes:0 (0.0b)

---

### Post by arolfsen on 2010-04-28
sudo lshw -C network:

*-network
   Description: ethernet interface
   product: DP83815 (macphyter) ethernet controller
   vendor: National Semiconductor Corporation
   physical id: 12
   bus info: pci@0000:00:12.0
   logical name: eth0
   version: 00
   serial: 00:0b:cd:a6:7c:77
   size: 10mb/s
   capacity:100mb/s
   width: 32 bits
   clock: 33MHZ
   capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt -fd 100bt - fd autonegiation
   configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10mb/s
   resources: irq:10 ioport:2400(size256) memory:d0004000-d0004fff memory:24000000-2400ffff(prefetchable)

*-network
    description: Wireless Interface
    physical id:2
    logical name: wlan3
    serial: 00:22:75:4f:7e:97
    capabilities: ethernet physcial wireless
    configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Iowan on 2010-04-29
I found a few other threads, but they were all pretty old. [This]("http://ubuntuforums.org/showthread.php?t=484976") was the most recent. 
Was that all the **lshw** info - it looks a little short...

---

### Post by arolfsen on 2010-05-01
yep. that was all that showed up

---

