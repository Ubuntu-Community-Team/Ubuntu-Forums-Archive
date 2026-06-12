---
title: "TV Card Breaks alsa-mixer"
date: 2010-04-22
forum: Multimedia Software
---

### Post by dealcorn on 2010-04-22
My TV card appears to break alsa-mixer with the log message:

"pulseaudio[1591]: alsa-mixer.c: Unable to load mixer: Invalid argument"

The sound card and TV card are:

```
:~$ lspci -vnn

00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
	Subsystem: Elitegroup Computer Systems Device [1019:2690]
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


03:04.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d0)
	Subsystem: Pinnacle Systems Inc. Device [11bd:002e]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

```

Outside of tvtime, sound works.  Is it possible to correct the invalid argument?

---

