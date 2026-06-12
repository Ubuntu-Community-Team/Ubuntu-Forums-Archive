---
title: "[SOLVED] Only mono sound with Alsa!"
date: 2008-12-08
forum: Multimedia Software
---

### Post by psychok9 on 2008-12-08
Hello!
I'm very happy of Ubuntu Intrepid 8.10, but i've discovered a **big bug/problem **with my soundcard: i get only **mono sound** on the front channels.
I've tried aplay with pulseaudio (and also killed), surround ogg music and fx... and is always the same problem. I get correctly surround separation, back-left and back-right, correct front-center... but i hear front-left on front-left and front right speakers, and the front-right voice on front-left and front-right speakers.

tested on: chan-id.wav, dolby-city.ogg, space_battle.wav etc.

Can you help me?
Thank you in advance.

```
05:01.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: Auzentech, Inc. Device 5431
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: CMI8788
	Kernel modules: snd-oxygen
```

---

### Post by psychok9 on 2008-12-08
Incredible... **Solved!** only a physical dual-stereo-jack connection problem!
I don't understand how... :confused:
Sorry to great Ubuntu and Alsa team!

---

