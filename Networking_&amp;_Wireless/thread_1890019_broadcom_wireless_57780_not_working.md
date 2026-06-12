---
title: "broadcom wireless 57780 not working"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by Sylos on 2011-12-02
Hello all.

Just bought a new laptop running a broadcom wireless card.

it is listed as follows:
```
 lspci -vvnn | grep 14e4
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04da]

```

windows uses the bcmwl664 driver.

I cant seem to get it to work. I tried b43 fwcutter but it had no effect.

Im not good with this sort of thing.

Can anyone offer any solutions?

Thanks

---

### Post by Sylos on 2011-12-02
Never mind. Used synaptic and went broadcom crazy installing anything that refered to broadcom. Seems to have done the job.

---

