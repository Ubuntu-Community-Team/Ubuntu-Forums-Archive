---
title: "How to get gigabit network on RTL8111/8168B card(s) ?"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by Zyprexa on 2011-07-27
I have this motherboard with RTL8111/8168B onboard lan adapter. And most of the time i only get 100mbit/s network on it. *It has happend though that sometimes it magically becomes gigabit card.*

I've tried several suggested solutions found with google, but it's still slow as before. So then i thought, well it must be something screwy with the adapter. So i got a brand new PCIe lan card installed. And wouldnt you know it, it had the same chipset and i'm now having the same problem with the PCIe adapter.


[LIST]
[*]I've installed the realtek driver from realtek's site
[*]I've blacklisted the module (**r8169**) mentioned in solutions found on the web
[*]I've tried ***sudo ethtool -s eth1 speed 1000 duplex full autoneg on***
[/LIST]
Is there really no way for me to get gigabit network on this chipset? None of the solutions i've found have worked.

when i run  **lshw -C network**

it shows **driver=r8168** on both adapters, which i think should be correct.  (before it showed **driver=r8169**)

Could someone please help me sort this out? :)

This is the output from lshw```

*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 54:e6:fc:80:12:4b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.024.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:41 ioport:b800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:21:54:ef:d9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.024.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 ioport:c800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vnet0
       serial: fe:54:00:37:25:88
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A link=yes multicast=yes port=twisted pair speed=10Mbit/s
```

---

### Post by bkratz on 2011-07-27
Are you using cat5 cable or cat5e/cat6 cable.  Cat5 is really only reliable to 100m while cat5e/6 is rated to 1000.

[http://www.infocellar.com/networks/cables/twisted-pair-cables.htm](http://www.infocellar.com/networks/cables/twisted-pair-cables.htm)

---

### Post by Zyprexa on 2011-07-27
Wellitywellitywellity, do i have an entire poultry farm on my face. :o
I set up another ubuntu server, and ran iperf between those two instead..And it appears that it's the other computer, [COLOR=Red]*with ****WINDOWS* **[COLOR=Black]running[/COLOR][/COLOR], that's causing the problem (eventhough it is also supposed to be gigabit motherboard)!:popcorn:
Ubuntu, i'm sorry i ever doubted you! Please remove this thread and bury it where no one will ever find it ;)

---

### Post by bkratz on 2011-07-28
> **Zyprexa said:**
> Wellitywellitywellity, do i have an entire poultry farm on my face. :o
I set up another ubuntu server, and ran iperf between those two instead..And it appears that it's the other computer, [COLOR=Red]*with ****WINDOWS* **[COLOR=Black]running[/COLOR][/COLOR], that's causing the problem (eventhough it is also supposed to be gigabit motherboard)!:popcorn:
Ubuntu, i'm sorry i ever doubted you! Please remove this thread and bury it where no one will ever find it ;)


Glad to hear you got it taken care of--enjoy!

---

