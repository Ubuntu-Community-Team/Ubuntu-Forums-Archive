---
title: "Wired/wireless ethernet speed decrease in multiples of 4, factors of 10?!"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by daveuu on 2010-01-25
Hi

When transferring files (>20Mb, not tested smaller) between two Ubuntu boxes the transfer rate becomes sluggish after initially starting well. Strangely the problem exists over wireless, wired, different ethernet chipsets (and drivers), through a router or by direct link, via ssh and nfs.

In detail: Over wireless NIC (Network controller: RaLink RT2561/RT61 802.11g PCI from Ubuntu 9.04 or 9.10, Athlon64 X2 at 2.8Mhz, 4GB PC2 8500 RAM) to router (Buffalo something running openWRT KAMIKAZE (8.09, r15789)) then router via wire to Ubuntu 9.09, Athlon64 X2 at 2.4 Mhz, 4GB moderate speed RAM (Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)) starts at approx 1.3 MB/s then drops to 40 kb/s after about 350MB

Over direct wire between same boxes (Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2) to Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01) or Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)) it starts at about 40 MB/s fluctuates down to 26 MB/s sometimes and after about 1670 MB settles on 400 kB/s

By my reckoning the router, NIC chipsets and drivers can be excluded leaving the PCI bus, processors, HDDs, OSes. All HDDs are SATA II which may be causing an initial limit of 40MB/s over the wire . . . the processors and RAM are fairly modern and not under load. Which leaves some sort of buffer or OS prioritising?

The strange thing is that the wireless and wired are both affected but by a factor of 10 which makes me think its less likely there is a hardware limitation and more likely there is a misguided daemon lurking somewhere.

Either way I'm stumped so any suggestions are very welcome

DaveUU

---

