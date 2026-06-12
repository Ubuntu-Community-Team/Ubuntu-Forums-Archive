---
title: "Wireless on Hp mini 210"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by silliej on 2011-02-17
I installed ubuntu Netbook version 10.10 3 weeks ago on my hp mini210.

after I installed it, my wireless won't work. And still after folowed several guides, still my wireless isn't working

when I use the command ¨sudo iwlist scan" in terminal, I see several networks but my card won't connect with them.

```

specs of my wireless card

[code]lshw -C network
``` *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:96:56:d4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:56000000-56003fff
[/code]I've tried any form of installing the broadcom STA driver, by the terminal and the regular installation.


somebody who knows the solution for this problem?

thanks,

Silliej

---

### Post by silliej on 2011-04-02
Still this problem, 

somebody got another vieuw on it than i have?

thanks,

---

