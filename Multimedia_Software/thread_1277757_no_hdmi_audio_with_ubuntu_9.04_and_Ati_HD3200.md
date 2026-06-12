---
title: "no hdmi audio with ubuntu 9.04 and Ati HD3200"
date: 2009-09-28
forum: Multimedia Software
---

### Post by Moae on 2009-09-28
Hi all, i try with all the solutions posted in this forum but i couldn't enable hdmi audio

with 

```
aplay -l
```

i can't see  
```

card 0: Ati [HDA ATI], device 3: ATI HDMI [ATI HDMI]  
Subdevices: 1/1  
Subdevice #0: subdevice #0 
```

i tried all, removing alsa, install alsa completely again, install pulseaudio and removing it
i need a lot of help eheheh

---

### Post by Moae on 2009-09-29
i see just this, and nothing else i can't play sounds from speaker television in any way

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

whit lspci -v i see this as audio device:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASRock Incorporation Device 0397
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at fe7f4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

who can help me?

---

### Post by Moae on 2009-09-29
Solved, I had the HDMI HD audio disable from BIOS

---

