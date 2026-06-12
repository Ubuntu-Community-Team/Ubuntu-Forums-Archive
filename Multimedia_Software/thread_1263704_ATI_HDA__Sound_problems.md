---
title: "ATI HDA  Sound problems"
date: 2009-09-11
forum: Multimedia Software
---

### Post by speel on 2009-09-11
I searched far and wide on the forum and came upon a ton of threads regarding my problem..but none of them seemed to work. I really can't get this sound card to work and perhaps some one can help me. Here is some info on it.

lspci -v
```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```

---

### Post by tkoco on 2009-09-21
Please try ```
aplay -l
``` and report back the findings.

> **speel said:**
> I searched far and wide on the forum and came upon a ton of threads regarding my problem..but none of them seemed to work. I really can't get this sound card to work and perhaps some one can help me. Here is some info on it.

lspci -v
```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```

---

### Post by raboofje on 2009-09-22
> **speel said:**
> I really can't get this sound card to work

```
Kernel modules: snd-hda-intel
```

'aplay -l' output would indeed help. 

What kind of problems are you experiencing? Which application did you use to try and play audio? What happened?

---

