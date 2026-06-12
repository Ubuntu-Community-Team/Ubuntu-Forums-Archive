---
title: "wireless established but can surf the Internet"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by halizah on 2009-12-20
Hi,
   I'm quite new to Ubuntu OS. I've upgraded my laptop from Ubuntu 9.04 to 9.10. I can't connect to the Internet even though wireless connection has been established. When with 9.04, wireless is too slow. Please help. Below is the info of my Ethernet:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 31
        I/O ports at 3000 [size=256]
        Memory at d5010000 (64-bit, prefetchable) [size=4K]
        Memory at d5000000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d5020000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

Cheers,
Liza

---

### Post by halizah on 2009-12-20
Oppps.. the title should be "wireless established but CAN'T surf the Internet". Sorry for that.

---

### Post by teward on 2009-12-20
the info for your ethernet won't help much. post the output of ```
lspci
``` and we'll find your wifi card.

---

