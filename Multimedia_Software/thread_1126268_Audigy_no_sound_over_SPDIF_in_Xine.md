---
title: "Audigy no sound over SPDIF in Xine"
date: 2009-04-15
forum: Multimedia Software
---

### Post by piusvelte on 2009-04-15
Solved:

Nevermind, this had to do with my soundcard configuration in LinuxMCE for the Media Director. Thanks!

***

Hi, I've been searching, reading and troubleshooting this for about 2 weeks, but can't figure it out.

I'm using an Audigy card connected to a Dolby Digital and DTS capable receiver over SPDIF coax. I'm running Kubuntu 7.10 with the latest alsamixer. In alsamixer, Optical Raw is muted and Analog/Digital Output is unmuted. If I change these in any way, mplayer won't play sound.

When I play a DVD with MPlayer, I get sound out of all speakers. 

Xine produces no sound at all. The receiver normally shows all 6 speakers lit up. When I start Xine, they all go out. If I turn up the volume, it displays "DEC.ERROR".

I've been trying different options in ~/.xine/config:
audio.output.speaker_arrangement:Pass Through
audio.device.alsa_passthrough_device:default

In MPlayer, I made these changes:
ao=alsa,alsa1x,
ac=hwac3,

Is anyone able to use Xine with an Audigy card and get sound? Please, any help would be great. Thank you!

---

### Post by markbuntu on 2009-04-15
I believe tha audigy can do either analog or digital but not both at the same time.

---

### Post by piusvelte on 2009-04-15
> **markbuntu said:**
> I believe tha audigy can do either analog or digital but not both at the same time.

The Analog/Digital setting is a switch in alsa. That's the label, not that I'm trying to play both at the same time. MPlayer plays the DVD fine, I'm just trying to get Xine to do so as well. Sorry for the confusion.

---

