---
title: "Network Card Not Recognized"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by Gurn5 on 2011-06-11
I just installed 11.04 and it doesn't see my Bigfoot Networks Killer Xeno Pro network card.  It recognizes the built in network adapter.  I tried disabling the built in adapter in the bios, but then it doesn't find any network card.  Do I need to find a driver for my card or is there some other solution.  The Bigfoot card works fine under Windows 7, where I use it for gaming.  I'd rather not have to switch the cable every time I switch operating systems.

---

### Post by superduperlinuxperson on 2011-06-12
run lspci -vnn | grep 14e4 and tell me what the output is

---

### Post by Gurn5 on 2011-06-12
It gives no output at all.

If I do lspci -vnn (no grep) the only entry I see that refers to Bigfoot Networks is

0a:00.0 Power PC [0b20]: Freescale Semiconductor Inc Device [1957:00b6] (rev 12)
    Subsystem: Bigfoot Networks, Inc. Device [1a56:1101]
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at f2c00000 (32-bit, non-prefetchable) [size=1M]
    Memory at f2dff000 (32-bit, non-prefetchable) [size=4K]
    Memory at f1000000 (64-bit, prefetchable) [size=16M]
    Memory at f2df8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

---

