---
title: "USB Headset"
date: 2009-07-25
forum: Multimedia Software
---

### Post by unforgiven512 on 2009-07-25
I would like to have Ubuntu automatically route sound to/from my USB headset when plugged in (preferably through ALSA), and through my onboard (snd-cs46xx) when the USB headset is unplugged.

Is there any way to do this easily??

Also, the volume control on my headset, it triggers the OSD, as if it were actually adjusting the volume, but it just doesn't adjust the volume.

Any ideas? Any tips or pointers??

I've read through multiple threads and various forums, I have yet to find a decent solution.

Thanks!

---

### Post by bcschmerker on 2009-07-25
I happen to be experimenting with a SIIG USB SoundWave 7.1 Pro in Ubuntu 8.04-LTS Hardy (LinUX Kernel 2.6.24-24-generic), and unfortunately an automatic mechanism for switching audio sources and sinks doesn't exist in PulseAudio, at least in Ubuntu versions up to 9.04 Jaunty; such a feature may be under test for 9.1beta8 Karmic or consideration for the yet-undeployed 10alpha1 Lucid.

Currently ASoundConf-GTK is used to select the default audio device; with both my planar Realtek ALC889 sound chip active and the SIIG plugged in and ready, options on my system include SB (planar audio), Default (viz., USB Audio), HDMI (viz., audio support in my planar ATI/Advanced Micro Devices Radeon HD3200), and PulseAudio.  Be advised that ALSAMixer from the console will only control the default mixer selected in ASoundConf-GTK, and GNOME ALSA Mixer does not access all controls for USB or planar HD audio.

Update:  9.10 is released, 10alpha1 Lucid available for testing.

---

