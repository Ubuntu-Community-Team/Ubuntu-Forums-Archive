---
title: "Network card speed issues"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by GrayFoxi0n on 2010-03-23
Lets see if anyone can help me to have a look on some issue im having since a long time ago.
I have a small computer (before it actually wasa firewall) with an 80 Gb disk, and one single processor 700Mhz more or less... 128 MB RAM that can run a headless ubuntu server perfectly... i access via ssh and so....
The thing is that i *think* that the network speeds it reaches in LAN are not quite enough to what it should be.
On the other side, in the same network, and connected via the same router, i have a computer running arch linux 64bit
Whenever i start any transfer via sftp (the most common way i use for managing any data i have on it) I see in netspeed (gnome's applet) that the speed the transfer reaches is never greater than 2 MiB/s - How can i know if the network speed is correct to a supposed 100Mbps network?
According to what another computer in the same network reports (windows XP btw), the network should have this speed... so, am i not supposed to get something like 10 Mb/s speeds?
If so, how can i check wheter the network card hardware is correctly configured?


I have this info, just in case is useful:

```
        *-network:0
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 10
             serial: xx:xx:xx:xx:xx:xx <- edited by op
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:12 ioport:d800(size=256) memory:e8000000-e80000ff memory:10100000-1010ffff(prefetchable)
```



dmesg | grep 8139 gave me this:

```
dmesg | grep 8139
[    3.839009] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.839143] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.839199] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.839246] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.014302] 8139too Fast Ethernet driver 0.9.28
[    4.014518] 8139too 0000:00:08.0: PCI INT A -> Link[LNKA] -> GSI 12 (level, low) -> IRQ 12
[    4.018263] eth0: RealTek RTL8139 at 0xd800, 00:40:f4:89:da:af, IRQ 12
[    4.019900] 8139too 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    4.096648] eth1: RealTek RTL8139 at 0xdc00, 00:40:f4:89:da:ae, IRQ 10
[    4.098371] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    4.103053] eth2: RealTek RTL8139 at 0xe000, 00:40:f4:89:da:ad, IRQ 11

```

I made it to unload the module 8139cp and only load the one named8139too but i get the same speed issues..... can anyone help me?

Thanks!

---

