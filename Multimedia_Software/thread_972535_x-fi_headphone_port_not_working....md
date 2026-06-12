---
title: "x-fi headphone port not working..."
date: 2008-11-05
forum: Multimedia Software
---

### Post by diggs on 2008-11-05
Hai guys.

My setup: Creative X-fi with the fancy pants panel on the front that you can plug guitars and crap into. It also has a headphone out jack. AMD socket 939 3800 dual core processor, asus a8n mobo. I'd provide a link to the creative product but their site is down.

When I first started this afternoon I had no sound, so I disabled my onboard sound card and followed the documentation on the ubuntu help site in order to get the x-fi running. I have two sets of speakers, one set plugged into the PCI slot and the other plugged into the front panel where there's a headphone port. The set plugged into the PCI card works no sweat.

```

lspci -v

05:06.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at a000 [size=32]
	Memory at d4000000 (64-bit, non-prefetchable) [size=2M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: oss_sbxfi


```

If someone could help me out that would be awesome. It's for my home theatre setup, if I cannot get the one set of speakers going I'll have to go back to windows LOL

---

### Post by diggs on 2008-11-06
I should also mention I'm running 8.10.

---

### Post by diggs on 2008-11-06
anyone?

---

### Post by diggs on 2008-11-07
please?

---

### Post by Psychopsia on 2008-11-14
The headphone plug in front panel?
the current driver dont support the console yet.

I have this problem too with inputs and knobs :(

---

