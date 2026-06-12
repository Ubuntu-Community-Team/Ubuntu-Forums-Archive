---
title: "Missing audio"
date: 2009-12-14
forum: Multimedia Software
---

### Post by TypeM on 2009-12-14
I dont have sound and get an error when i play mplayer

> Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
===========================================
[AO ESD] esd_open_sound failed: Connection timed out
Failed to initialize audio driver 'esd'
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1920x1080 => 1920x1080 MPEG-2 VA API Acceleration 
[VD_FFMPEG] XVMC-accelerated MPEG-2.
V:  29.4 882/882 21%  7%  0.0% 0 0

When i type aplay -l i gett following.
> **** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and this  lspci -v gives following (audio only)
> 00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
	Subsystem: Intel Corporation Device 8119
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b0050000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

 I' tried to use the "Comprehensive Sound Problem Solutions Guide v0.5e" and still cant get any audio. Checked that sound is not muted (alsamixer) 

Also uninstalled pulseaudio.

Dont know what to do next

---

### Post by TypeM on 2009-12-22
Strange problem.

I tested some now, and found that i have sound!!! But i only in my headphones but not the speakers in the built in my lcd screen.

But when i use Windows XP i have sound in the speaker in my LCD screen.

Does anyone have a clue  ?

---

### Post by RedSingularity on 2009-12-22
Did you have sound coming out of the speakers a while back?

---

### Post by TypeM on 2009-12-22
No i never had sound, and this (9.10) is the first  ubuntu version om this machine, cause i bought it after 9.10 was released.

short XP = audio in speakers and headphones.
Ubuntu 9.10 = No audio in speakers BUT audio in headphones

Strange  Headphones works but not speakers...

---

### Post by RedSingularity on 2009-12-22
In terminal type 

alsamixer

and make sure the volume is all the way up.

---

### Post by TypeM on 2009-12-29
Now i have audio, Does anyone know why i need to push volume in alsamixer all the way up? the sound doesn't sound so great.

(by the way thanks)

---

