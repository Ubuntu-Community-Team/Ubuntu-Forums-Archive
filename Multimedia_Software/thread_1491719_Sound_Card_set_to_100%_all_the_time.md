---
title: "Sound Card set to 100% all the time"
date: 2010-05-23
forum: Multimedia Software
---

### Post by Simon Cropper on 2010-05-23
Hi,

**Background **

I have a Intel Motherboard with on-board sound card by realtek. I have tried everything over the last few months to get the system to operate with this chipset. The best I got was the very quiet output where the system needed to be cranked up to 100%+ to make the sound even audible. I upgraded from Ubuntu 9.10 to 10.4 and the issue still persists. 

I acquired a soundcard and put this in the machine and bang I now have full sound. No setup or configuration. The problem is, is that the sound card defaults to 100% volume, so everytime I log on the system I nearly get blown out of my chair. I have changed the various settings via PulseAudio, AlsaMixer and Gnome Alsa Mixer, and read an inordinate number of webpages and search everywhere on the web but with no success.

**Desired solution**

Get sound card to startup at ~50% volume. 

Note that I have used "sudo alsactl store 0/1" to save the configuration when the volume is lower but this does not have an impact.

**Blurb on system for the brighter people among you...**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Intel Corporation Device 0002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at e3220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

07:02.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
	Subsystem: ESS Technology Device 8898
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at 1000 [size=64]
	I/O ports at 1050 [size=16]
	I/O ports at 1040 [size=16]
	I/O ports at 1064 [size=4]
	I/O ports at 1060 [size=4]
	Capabilities: <access denied>
	Kernel driver in use: ESS ES1938 (Solo-1)
	Kernel modules: snd-es1938

---

