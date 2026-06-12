---
title: "alsamixer confusion"
date: 2009-04-18
forum: Multimedia Software
---

### Post by jim1964 on 2009-04-18
I'm confused by all the settings offered by alsamixer. Can someone please explain what the various devices are? Here are the details.

I have a Dell 1545 laptop.
lspci -v gives the following info:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 02aa
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6afc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

From alsa mixer:
Card: HDA Intel
Chip: IDT 92HD71B7X

Here are the alsamixer devices listed. Some let me set a level, other are an on/off switch and others offer me options to choose from. I mostly need help identifying the one's with an asterisk (*). But any info would be OK. Thanks.

The playback devices listed are:
Master (set level)
Headphone (set level)
PCM (set level)
Front (set level)*
IEC958 (on/off switch)*
IEC958 Default PCM (on/off switch)*
Analog Loopback (on/off switch)*
Analog Loopback 1 (on/off switch)*
Digital Input Source (options: Digital Mic 1, Mixer, Analog Inputs)
PC Beep (set level)

The capture devices listed are:
Capture (set level)
Capture 1 (set level)*
DAC0 (set level)*
DAC1 (set level)*
Import0 Mux (set level)*
Import1 Mux (set level)*
Input Source (options: Front Mic, Mic)
Input Source 1 (options: Front Mic, Mic)*
Mux (set level)*
Mux1 (set level)*

---

