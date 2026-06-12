---
title: "meerkat"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by sasha23 on 2010-10-12
I have an old uniwell laptop with plenty of resources to run meerkat. Ubuntu 10.10 installs file but the wireless pcmcia card is not recognized. Odd thing is that it does work with 10.04. Typing
lspci -vnn

I get

00:0b.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
    Subsystem: Uniwill Computer Corp Device [1584:3002]
    Flags: bus master, stepping, slow devsel, latency 168, IRQ 5
    Memory at 28000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 20000000-23fff000 (prefetchable)
    Memory window 1: 24000000-27fff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

Does anyone know of a driver for this?

---

