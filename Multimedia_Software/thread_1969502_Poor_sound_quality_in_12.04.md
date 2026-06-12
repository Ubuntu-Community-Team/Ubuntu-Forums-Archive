---
title: "Poor sound quality in 12.04"
date: 2012-04-30
forum: Multimedia Software
---

### Post by Superserial on 2012-04-30
Sound card: Soundblaster live 5.1

After some updates a day or two ago in 11.10 (32bit) sound stopped working. I found out it was possible to get it to work again by pressing mute and unmute in pulse audio volume controll or whatever it is called.

However sound quality is really bad now. No bass, cracks, max volume is maybe 30% of what was before that. It sounds like played through some cheap toy radio.

I reinstalled clean xubuntu 12.04 (64 bit) and problem still persists.

I searched for answers and found no solution. I remember I tried editing default.pa in pulse folder to change interrupt mode, I also checked sample rate (its 44100). I know there is no solution for now, I just wanted to inform that problems are also on my sound card.

Thanks.

---

### Post by brainwash on 2012-04-30
Did you switch to *Analog Surround 5.1 Ouput* (Volume Control > Configuration)?

Furthermore, you could try to increase the Master and/or PCM volume directly using alsamixer:
```
alsamixer
```

Well, the most annoying thing, the crackling noise, has been caused by the proprietary ATI/AMD fglrx driver. I had to disable hardware acceleration (display compositing, xrender) to get clean sound.


```
Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
Subsystem: Creative Labs SB Live! 5.1 Digital OEM [SB0220]
Flags: bus master, medium devsel, latency 32, IRQ 16
I/O ports at dc00 [size=32]
Capabilities: <access denied>
Kernel driver in use: snd_emu10k1
Kernel modules: snd-emu10k1
```

---

### Post by Superserial on 2012-04-30
Everything in pulse/alsa is maxed out.
I tried various stereo/surround outputs, no difference.
That machine uses nvidia.

---

