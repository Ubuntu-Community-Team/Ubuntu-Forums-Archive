---
title: "No sound in after switching to esound."
date: 2009-08-25
forum: Multimedia Software
---

### Post by feedmecereal on 2009-08-25
PulseAudio just doesn't seem work on my Dell computer. I switched to Esound and that mostly works except that there is no sound in. Because of this, Skype is unusable. I did find an OSS version of Skype and it partially works but it just doesn't seem to pick up my voice on the test call.

I was able to get all sound to work fine at some point before my hard drive died. But now, since I have reinstalled Ubuntu, I can't seem to get all the sound working perfectly.

I'm not exacly sure what info you might need from me so I'll just include the output of lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01dd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: oss_hdaudio
	Kernel modules: snd-hda-intel
```

---

