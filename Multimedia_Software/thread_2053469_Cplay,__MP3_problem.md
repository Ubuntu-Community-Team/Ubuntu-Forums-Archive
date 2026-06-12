---
title: "Cplay,  MP3 problem"
date: 2012-09-05
forum: Multimedia Software
---

### Post by MoonCactus on 2012-09-05
Same issue on my PC.

It's weird because mpg123 or aplay do work fine. But since my upgarde to ubuntu 12.04 LTS Release i386 (20120423), cplay no more produces sound (it did work before!)

It just skips the mp3 quickly (~2 seconds each), with no error and no sound, and I am starting to lack ideas on how to fix the issue...

I just love how it simply plays mp3 files in folders. Period ;)
I do NOT have all the proper ID3 tags on my tracks, so 99% of the other players are either useless or cumbersome to me, eg. where's the damn file name to delete songs I dislike? or why do they always parse my whole library where I just can use "find" ;)


```
#uname -a
Linux erfoud 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
```

```
#lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
```

---

### Post by nothingspecial on 2012-09-05
Question moved out of old solved thread to one of it's own.

---

