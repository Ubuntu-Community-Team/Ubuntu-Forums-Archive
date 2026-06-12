---
title: "Help! Sound in VLC but not in songbird, flash etc"
date: 2009-02-09
forum: Multimedia Software
---

### Post by thecc on 2009-02-09
Hello,

I've recently installed Ibex and it worked fine out of the box until yesterday. For some reason sound playback died except for (as far as I can tell) in VLC. Songbird plays the file but I can't hear any thing. Flash does not have sound either.

When I click the test button in Sound Preferences all I get are some loud hisses and pops.

I'm guessing it has something to do with pulseaudio. Did a few guides on here but those didn't help at all. Reinstalled it, removed it, tried to go around it etc.


Some info:

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01d8
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

One more thing to note is that in the Client Tab of the PulseAudio Manager window this text keeps flashing on/off.

```
 ALSA Plugin [python 2.5] 
```


Pulseaudio seems to be causing a lot of problems for a lot of people and I can't help but think it might be a bit overkill for a desktop machine? I have no need to push or stream sound over a network, I just want to play some music!

Thanks in Advance,

EDIT:

I just tried to play an MP3 in VLC and looks like VLC is joining the Hiss and Crack crowd as well. I now have no sound at all...

---

