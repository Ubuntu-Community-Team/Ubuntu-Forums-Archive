---
title: "Sound quit working; OK under Windows"
date: 2010-07-09
forum: Multimedia Software
---

### Post by ozark_hillbilly on 2010-07-09
Anybody got a tip on how to troubleshoot lost audio?
Works under DOS windows and has been working under Ubuntu for a long time.
Running sound check under Preferences> Sound results in hearing static on speakers. I only get a low decibel static sound when Ubuntu boots up and I log on.

******************************
ed@House:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
********************************
lspci -v  (partial output)

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82ea
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
****************************************

Is it an ALSA or PulseAudio problem?
Are these still pertinent:

There are two systems that must work in order for Ubuntu to play sound, Alsa and PulseAudio.

To fix alsa problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

To fix pulseaudio problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Any help appreciated,
Ed

---

### Post by ozark_hillbilly on 2010-07-09
Man do i feel like a dumbass..

ALSA mixer PCM slidebars were moved down somehow....

duh,

Ed

---

### Post by lidex on 2010-07-10
Can you mark the thread as solved using 'Thread Tools' up top please? Glad you got it working ;)

---

