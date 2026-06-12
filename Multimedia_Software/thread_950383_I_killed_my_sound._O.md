---
title: "I killed my sound. :O"
date: 2008-10-17
forum: Multimedia Software
---

### Post by hakuchuumu on 2008-10-17
At first I had quiet sound with ALSA, and proceeded to try the OSS guide. That left me with NO audio, so I deleted the parts from the blacklist and purged my sound set up and reinstalled ALSA as per the Comprehensive Sound Problem Solutions Guide. Other than reinstalling, what do I do? 

So, I have an Intel HDA card, which shows from lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Sony Corporation Unknown device 81e7
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 4c300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

But when I run aplay -l I get no soundcards found.

---

### Post by hakuchuumu on 2008-10-19
Come on guys, does nobody have any idea? :(

---

### Post by Yellow Pasque on 2008-10-19
Try the ALSA script here: [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by hakuchuumu on 2008-10-21
I ended up reinstalling 8.04. So we're back to quiet sound.

---

