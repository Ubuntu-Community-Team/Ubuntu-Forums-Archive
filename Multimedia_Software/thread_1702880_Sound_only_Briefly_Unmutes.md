---
title: "Sound only Briefly Unmutes"
date: 2011-03-08
forum: Multimedia Software
---

### Post by bcollier on 2011-03-08
I am using my headphones in ubuntu 10.10 and in the sound preferences the box next to mute is checked.  I can uncheck the box and hear about a half second of the music playing before it automatically mutes again.  Once I was able to get about a minute of sound before it automatically muted, and could not be unmuted.  I'm using the built in sound from my Asus P5K Pro I believe.

I tried searching through forums and guides but couldn't find anything similar to this problem.  My drivers seem to be fine since I can play a minute or so of music.  I also tried different headphones in the jack, same problem.  

Any help would be appreciated, some of my sound-related output is below.


sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

sudo lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: ASUSTeK Computer Inc. Device 83ae
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at f5ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

