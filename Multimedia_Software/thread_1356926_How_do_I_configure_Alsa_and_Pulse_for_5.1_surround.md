---
title: "How do I configure Alsa and Pulse for 5.1 surround"
date: 2009-12-16
forum: Multimedia Software
---

### Post by Baasha on 2009-12-16
I am running Karmic 9.10 64 bit.  I have Alsa and Pulseaudio installed with a 5.1 external sound system.  I can't figure out how to change Alsa and Pulsaudio from the present stereo duplex output to 5.1 output.  There don't seem to be any other options in either Alsa or Pulseaudio.  I have followed several lengthy threads on this forum but nothing has worked so far.  I also periodically lose sound altogether and have to do a "sudo modprobe snd-hda-intel" to get it back.  It seems like every time there is a kernel update I lose audio and video and have to spend days getting it all back again, and I never have been able to get 5.1 sound working.  Any help would be appreciated.

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
lspci -v
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 8375
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

