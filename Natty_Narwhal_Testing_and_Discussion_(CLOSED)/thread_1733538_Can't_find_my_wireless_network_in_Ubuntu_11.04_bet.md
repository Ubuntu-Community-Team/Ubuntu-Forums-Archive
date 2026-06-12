---
title: "Can't find my wireless network in Ubuntu 11.04 beta2"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Anutesyn on 2011-04-19
Hi!

I've tried 11.04 a few times (the alpha and beta releases) and every time I've had problems with connecting to my wireless network. I've had no problem connecting to it with 10.10, and my Windows partition has no problems with finding the network. So I've drawn the conclusion that there's something with 11.04 that causes this problem. 

```
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

Might add that that wired network has worked in 11.04

edit: Might've forgotten to mention that I can find all of my neighbors networks but mine is missing from the "Wireless Networks"-list.

edit:

```
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
	Subsystem: Hewlett-Packard Company Device 1508
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

---

### Post by Anutesyn on 2011-04-23
This is solved. Reset the router back to factory settings then recreated the wireless network. Only then did it manage to find it so that I could connect to it.

---

### Post by teachop on 2011-04-23
> **Anutesyn said:**
> This is solved. Reset the router back to factory settings then recreated the wireless network. Only then did it manage to find it so that I could connect to it.
Are your security settings different now, or do you think the router was just mixed up?

---

