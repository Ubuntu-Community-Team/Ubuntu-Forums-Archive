---
title: "thinkpad W500 sound just stopped"
date: 2008-12-08
forum: Multimedia Software
---

### Post by Bashar &quot; on 2008-12-08
hello,
i use 8.10 and sound was working few days back, not sure what got updated and sound no longer works

lspci:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


lspci -v:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20f2
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at fc220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

please advise

---

### Post by glotz on 2008-12-08
Seen this? [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by antmo on 2008-12-08
i also have a w500 and i noticed that when you hit the hardware mute button, it doesn't indicate anything in the gui element about being muted, but it does mute.  however, pressing it again does not unmute... you simply need to adjust the volume up or down once from the hardware buttons and it will unmute.

hope this helps.

mjb

---

### Post by Bashar &quot; on 2008-12-09
i fixed sound by installing latest alsa snapshot , but still no mute gui icon when pressing and can't unmute

---

