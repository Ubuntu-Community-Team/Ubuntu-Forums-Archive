---
title: "PCI Network card works in Jaunty, fails in Koala: RTL8111/8168B"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by klotz on 2009-11-11
My PCI network card worked with Ubuntu 9.04, but it fails in 9.10.
I've noticed that I get a "no link" message from mii-tool.

I can get it to work under 9.10 by booting Koala with with the old kernel 2.6.28-16.  It fails to work if I boot Ubuntu 9.10 with its stock kernel 2.6.31-14.

The card is an Allied Telesis optical fiber card.  lspci reports it like this:

05:00.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 02)

Although it's a fiber card instead of a UTP card, I'm not aware of any special driver issues associated with the physical media layer.

---

### Post by klotz on 2009-11-11
lshw -C network output from 2.6.28-16 (working case):
```

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:0a:a5:ab
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet phys
ical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversio
n=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:2299 ioport:b000(size=256) memory:ea000000-ea000fff memory
:ed200000-ed21ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:00:f4:a2:98:41
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 
100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion
=3.5.23-k6-NAPI duplex=half firmware=N/A ip=64.139.9.139 latency=64 link=yes max
latency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ed000000-ed000fff(prefetchable) ioport:c000(size
=32) memory:ec000000-ec0fffff memory:eb000000-eb0fffff(prefetchable)

```

lshw -C network output from 2.6.31-14 (failing case):
```
  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:0a:a5:ab
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet phys
ical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversio
n=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:b000(size=256) memory:ea000000-ea000fff memory:e
d200000-ed21ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
      physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:00:f4:a2:98:41
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 
100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion
=3.5.24-k2-NAPI duplex=half firmware=N/A ip=64.139.9.139 latency=64 link=no maxl
atency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ed000000-ed000fff(prefetchable) ioport:c000(size
=32) memory:ec000000-ec0fffff memory:eb000000-eb0fffff(prefetchable)

```

diff:
```

diff lshw-2.6.28-16.txt lshw-2.6.31-14.txt 
16c16
<        resources: irq:2299 ioport:b000(size=256) memory:ea000000-ea000fff memory:ed200000-ed21ffff(prefetchable)
---
>        resources: irq:28 ioport:b000(size=256) memory:ea000000-ea000fff memory:ed200000-ed21ffff(prefetchable)
31c31
<        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A ip=64.139.9.139 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
---
>        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=64.139.9.139 latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s

```

---

### Post by klotz on 2009-11-11
FYI I have tried a different fiber card with the AMD 79c970 chipset [PCnet32 LANCE driver] and it works with Koala.  So this problem is limited to the Intel 82557/8/9/0/1 Ethernet Pro 100 chipset version of the fiber card.

---

