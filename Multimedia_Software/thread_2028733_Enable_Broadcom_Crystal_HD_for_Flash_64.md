---
title: "Enable Broadcom Crystal HD for Flash 64"
date: 2012-07-18
forum: Multimedia Software
---

### Post by leach on 2012-07-18
Just wonderng if anyone has any thoughts as to what could be going wrong. I can get my Broadcom Crystal HD card to work with xbmc but no such luck with flash videos.

I've added 

```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true 
```
to /etc/adobe/mms.cfg with no luck.

my dmesg output looks like

```
leach@dot ~ $ dmesg | grep crystalhd
[   13.951919] Loading crystalhd v3.10.0
[   13.951988] crystalhd 0000:03:00.0: Starting Device:0x1612
[   13.952138] crystalhd 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.959639] crystalhd 0000:03:00.0: irq 44 for MSI/MSI-X
[   14.265884] crystalhd 0000:03:00.0: setting latency timer to 64
```

I'm at an impasse, any ideas?

---

