---
title: "Sound skipping with new sound card"
date: 2010-03-02
forum: Multimedia Software
---

### Post by feedmecereal on 2010-03-02
I had terrible audio problems with the on-board sound with my Dell so I eventually decided to buy a new sound card. I bought a really cheap one off eBay from China (say what you want).

I had some trouble getting it to work but someone in an Ubuntu chat room helped me a lot. The only problem that I am having now is that it seems to skip and pause with everything I play. This makes the audio very difficult to listen to.

After a couple of chat rooms I got to the steps at this page: [http://www.pulseaudio.org/wiki/BrokenSoundDrivers]("http://www.pulseaudio.org/wiki/BrokenSoundDrivers"). I am stuck at the command:
```
./alsa-time-test hw:0 > log 
```
where I get this error message:
```
alsa-time-test: alsa-time-test.c:189: main: Assertion `(unsigned) avail <= buffer_size' failed.
```

Here is the output of lspci -v:
```
03:03.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
	Subsystem: ESS Technology ES1978 Maestro 2E
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ES1968 (ESS Maestro)
	Kernel modules: snd-es1968, radio-maestro

```

---

