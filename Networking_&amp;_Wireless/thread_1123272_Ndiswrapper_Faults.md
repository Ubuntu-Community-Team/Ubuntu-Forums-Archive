---
title: "Ndiswrapper Faults"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by Trafficflow on 2009-04-12
Can anybody tell me what this means? I think the WG111t will not work on this to good. I guess I need to look in to a new one.

iswrapper (NdisWriteErrorLogEntry:193): code: 0xdd331e00
[   20.783178] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x28
[   20.783186] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xe0b80000
[   20.783195] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xe0b80000
[   20.784724] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   20.784740] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   20.784779] ndiswrapper (mp_halt:262): device ddde2480 is not initialized - not halting
[   20.784788] ndiswrapper: device eth%d removed
[   20.784848] ndiswrapper: probe of 4-1:1.0 failed with error -22

---

### Post by cariboo on 2009-04-12
There is a driver in the kernel for your device, it is called natsemi. Have you check to see if the driver is loaded? To check open an Applications-->Accessories-->Terminal and type:

```
lsmod | grep natsemi
```

This should tell you if the driver is loaded.

If you could paste the output of:

```
sudo lshw -C network
```

in your next post, it would be a great help.

Jim

---

