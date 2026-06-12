---
title: "[SOLVED] Ubuntu can't find my sound card"
date: 2008-12-16
forum: Multimedia Software
---

### Post by securitynut on 2008-12-16
After doing an upgrade from 8.04 to 8.10, my sound card isn't being recognized. 

aplay -l displays: device_list:215: no soundcards found...

lspci -v displays: 

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 12
	I/O ports at a800 [size=32]
	Capabilities: <access denied>
	Kernel modules: snd-ca0106

Are the drivers not installed or is my sound card not recognized?

---

### Post by linux_tech on 2008-12-16
how about
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by securitynut on 2008-12-18
Here's what I get:

cat: /proc/asound/card0/codec#*: No such file or directory

---

### Post by securitynut on 2008-12-18
Don't have any clue what I did but it works now.

---

### Post by BroadArrow on 2009-01-06
> **securitynut said:**
> Don't have any clue what I did but it works now.

Still working OK? I've encountered the exact same symptoms...

---

