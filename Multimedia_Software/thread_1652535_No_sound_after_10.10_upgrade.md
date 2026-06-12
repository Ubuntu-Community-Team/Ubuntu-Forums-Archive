---
title: "No sound after 10.10 upgrade"
date: 2010-12-25
forum: Multimedia Software
---

### Post by Badbunny on 2010-12-25
Hello, 
I just upgraded from 10.04 and lost sound.

aplay -l gives me
```
aplay: device_list:235: no soundcards found...
```

while lspci -v gives
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P5B
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

```

find /lib/modules/`uname -r` | grep snd
gives a whole lot of stuff, which I assume means I have the sound modules installed.

The soundcard worked just fine before the upgrade, so I assume this is a some kind of a configuration problem. Any help on this?

EDIT:
Now this is embarrassing. 
sudo modprobe snd-hda-intel
did the trick.

---

