---
title: "No Sound After Crash"
date: 2010-05-03
forum: Multimedia Software
---

### Post by z00s on 2010-05-03
So everything was working great in Lucid until my system crashed about 10 minutes ago.  After booting it back up I have no sound anymore.  I've got a Soundblaster Audigy that's been working in Ubuntu for years now.

Pulseaudio and Alsamixer are set how they should be (every volume meter around 80 and nothing muted).

aplay -l provides:

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v provides:

03:06.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at df00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

I even tried some unorthodox ideas such as completely shutting down via shutdown -h now.  I tried killing and restarting the pulseaudio daemon.  Anyone have any suggestions?  I've exhausted everything I can think of / have found in trying to get the sound working again.

---

### Post by z00s on 2010-05-04
Bump.

---

### Post by z00s on 2010-05-04
Bump.

---

