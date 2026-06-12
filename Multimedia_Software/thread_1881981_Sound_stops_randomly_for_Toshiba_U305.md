---
title: "Sound stops randomly for Toshiba U305"
date: 2011-11-16
forum: Multimedia Software
---

### Post by Kivrin on 2011-11-16
I've had Ubuntu for years, currently running Narwhal on my Ubuntu U305 laptop. Recently, the sound has started to go out mid-usage and won't come back unless I restart. I've had problems in the past where the sound was being monopolized by, say, Amarok, but this time it will just go out even if Amarok (or any other media program) is closed.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I've checked alsamixer and everything looks okay, but I'm not extremely linux-savvy, so I'd appreciate any advice. 

Thanks!

UPDATE

I've reinstalled alsa, maybe that will fix it.

---

### Post by Kivrin on 2011-11-17
UPDATE

I reinstalled alsamixer last night, and all was well. (But possibly only because I had to restart along the way.) I put my computer into hibernate and went to bed; this morning, the sound wasn't working. I read through the sound troubleshooting sticky and adjusted the sleep.d file to enable alsa when my computer comes out of hibernate. No sound, so I restarted.

Now my computer isn't reading the soundcard at all! 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****

```

Any ideas?

---

### Post by Kivrin on 2011-11-17
UPDATE II

I purged and reinstalled alsa, then went through modprobe. Still no sound. aplay -l is still empty. 

When I run alsamixer, I get a notice that "This sound device does not have any controls."

---

### Post by meditatingfrog on 2012-06-06
> **Kivrin said:**
> UPDATE II

I purged and reinstalled alsa, then went through modprobe. Still no sound. aplay -l is still empty. 

When I run alsamixer, I get a notice that "This sound device does not have any controls."

Hey, did you ever find out anything on this?  I have a u305 too, and wanted to sync up with you, maybe we can give each other info.  Be well.

---

