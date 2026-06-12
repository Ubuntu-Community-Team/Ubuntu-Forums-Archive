---
title: "Alsa Hardware mixing?"
date: 2010-08-15
forum: Multimedia Software
---

### Post by RedSingularity on 2010-08-15
Quick question......does ALSA support hardware mixing in 10.04?  I would like to remove pulseaudio but it currently supports that feature.  In previous versions of Ubuntu uninstalling pulse led to no hardware mixing.

---

### Post by RedSingularity on 2010-08-15
Well i guess i answered my own question.  I completely removed pulse and everything works fine.  Actually the sound quality is nicer without pulse.

---

### Post by bprins on 2010-08-15
[http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23](http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23)

not sure, but they do mention hwmixing.

---

### Post by RedSingularity on 2010-08-15
Yeah they do.......I wonder if this is recent though?  As i said, in earlier versions of Ubuntu i couldn't get HW mixing to work without pulse.

---

### Post by bprins on 2010-08-15
alsa 1.0.23 is default in ubuntu10.10, so you have to wait a little longer, or try to upgrade to alsa 1.0.23.

in karmic and lucid it's 1.0.21.

---

### Post by kostkon on 2010-08-15
I'll assume that you are now using dmix, the software mixer of alsa (inferior to PulseAudio), since nowadays few cards (and even fewer alsa drivers) support hardware mixing.

---

### Post by RedSingularity on 2010-08-15
Why would hardware mixing start becoming unavailable on audio cards?  The majority of people, I think, want to play multiple streams of audio at the same time.......say for example, talking to a friend on skype and watching a youtube video.  You would need a card that can support 2 streams correct?

---

### Post by Entity` on 2010-08-25
I have a somewhat related problem.  I seem to be incapable of utilizing all of my hardware capabilities.  My analog outputs are just fine, but my digital outputs are unavailable for some reason or another.  I would like to use my digital outputs but can't.  Any help would be appreciated.

I am using an MSI 870A-G54 motherboard and a lspci -v gives this:

```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
	Subsystem: Micro-Star International Co., Ltd. Device 7599
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fe6f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Also I would like to use the digital outputs and the analog outputs at the same time.

---

