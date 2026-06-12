---
title: "Constant background white-noise"
date: 2011-02-26
forum: Multimedia Software
---

### Post by oscar.broman on 2011-02-26
Hey guys,
I've got this constant background noise in my headphones, it sounds like when you set the volume really loud. I'm currently using Open Sound System; I had the same issue with the default sound drivers, that's why I installed oss in the first place.
Does anyone here have an idea of what's causing this?

I have a SoundMAX HD audio card on an ASUS-M3A32 motherboard.

ossinfo:
```
Version info: OSS 4.2 (b 2004/201101051743) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 (oscar-m3a32)

Number of audio devices:	9
Number of audio engines:	13
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=1093 (2435)
    HD Audio controller ATI HD Audio
    Vendor ID    0x10024383
    Subvendor ID 0x10438288
     Codec  0: AD1988B (0x11d4198b/0x1043829b)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio AD1988B (Mixer 0 of device object 1)

Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play rear                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
HD Audio play headphone           /dev/oss/oss_hdaudio0/pcm4  (device index 4)
HD Audio play spdifout-mix        /dev/oss/oss_hdaudio0/spdout0  (device index 5)
HD Audio rec rec1-src             /dev/oss/oss_hdaudio0/pcmin0  (device index 6)
HD Audio rec rec2-src             /dev/oss/oss_hdaudio0/pcmin1  (device index 7)
HD Audio rec rec3-src             /dev/oss/oss_hdaudio0/pcmin2  (device index 8)

Nodes
  /dev/dsp -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_hdaudio0/spdout0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0
```

peace!

---

### Post by oscar.broman on 2011-03-21
Hello me, it's me again.

The sound works without any strange background noise in the orange or black audio outlet, for some reason. I need only stereo output so I'm happy!
I'm guessing some sort of re-configuration of PulseAudio would make it output from the correct hole; but hey, if it ain't broke, don't fix it!

---

### Post by lookitseman on 2011-04-23
I would bet it's an electrical issue.  You're likely hearing the hum of electricity, amplified by your system's audio hardware.

Are you on a laptop?  If so, see if the issue still occurs when the laptop is not plugged into the wall.

Are there other devices plugged into your system which are also plugged into the wall?  Remove them from your system temporarily to see if that changes anything.

When I worked with audio installations, I kept a handful of $1 AC adapters handy which converted a 3-prong power plug into a 2-prong power plug.  I got mine at the local Home Depot.

**I'm sure the third prong served a purpose, so take this with a pinch of salt**, but that usually solved the issue.

---

