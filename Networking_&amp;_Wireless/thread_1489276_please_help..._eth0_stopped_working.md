---
title: "please help... eth0 stopped working?"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by mechanizedmedic on 2010-05-20
i installed and ran System Profiler & Benchmark ran a test. then i rebooted and turned off ACPI/PowerNow. at this point i realized my network card had gone down so i went back an turned the ACPI on. nothing changed. :( 

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:30:67:41:0a:91
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:fbfff000-fbffffff(prefetchable) memory:fbff8000-fbffbfff(prefetchable) memory:feae0000-feafffff(prefetchable)

---

### Post by mechanizedmedic on 2010-05-20
okay... i used a variety of fixes shown on other threads. nothing worked. i go to the fridge, crack open a beer. when i return 30 seconds later and open firefox just for the hell of it and everything works again except for the notification icon... i must be freakin out.:confused:

---

