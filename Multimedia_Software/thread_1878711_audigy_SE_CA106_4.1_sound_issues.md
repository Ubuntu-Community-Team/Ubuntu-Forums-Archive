---
title: "audigy SE CA106 4.1 sound issues"
date: 2011-11-10
forum: Multimedia Software
---

### Post by arrgghh on 2011-11-10
i'm on ubuntu 11.04 x64. i have a creative audigy SE with a CA106 (lspci output below) chip and i'm having some issues with pulseaudio.


i've found that a lot of people have problems with this exact hardware, but they seem to be having no sound at all: [http://ubuntuforums.org/showthread.php?t=1491560](http://ubuntuforums.org/showthread.php?t=1491560)
[http://openubuntu.com/index.php?topic=962.0](http://openubuntu.com/index.php?topic=962.0)
...


but i'm having specific problems with analog 4.1 output. my sound otherwise works fine.


here's what happens when i turn on 4.1 analog output over the sound manager and run audio:

* pulseaudio takes up 80-90% of one cpu core
* i have this weird crackling noise in very undefined intervals. it's like amplitudes would overload, but it's definitely not connected to the volume and / or the sound. i guess it could have something to do with the cpu load and/or latency issues.


now concerning sound and audio with gnu/linux, i'm totally lost in general.

any ideas?


here are some additional informations collected by the alsa-info script: [http://pastie.org/2841362](http://pastie.org/2841362)

lspci -v
```
05:05.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs SB0570 [SB Audigy SE]
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at e800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106
```

aplay -l
```
thomas@jack:~$ aplay -l
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
```



/add
from what i've read so far, support for the chip i'm using seems to be - n layman's terms - crap.

---

### Post by arrgghh on 2011-11-10
> **arrgghh said:**
> /add
from what i've read so far, support for the chip i'm using seems to be - n layman's terms - crap.

seems hold true. i found an no-name soundcard in my box of old hardware, and seems to work fine. no crackling, no massive cpu load.

i conclude: don't buy the Soundblaster Audigy SE, the low price seemed bogus all along :)

---

