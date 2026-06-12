---
title: "No network devices able to connect"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by agansert on 2013-02-15
I just built a file server with a Gigabyte 990FXA-UD3 motherboard with onboard ethernet.  I'm running 12.10.  

I don't get any connection with my onboard ethernet although it seems to be detected.  I've also tried an Intel PWLA8391 network card with onboard lan disabled but I get the same results.

Any ideas? I'm all out.

Here's my ifconfig output:
```
eth0      Link encap:Ethernet  HWaddr 94:de:80:0d:9c:54  
          inet addr:10.0.1.12  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fe0d:9c54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1222 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1057 (1.0 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:174912 (174.9 KB)  TX bytes:174912 (174.9 KB)
```

And here's my lshw -C network output:
```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:0d:9c:54
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=10.0.1.12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:75 ioport:b000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
```

---

