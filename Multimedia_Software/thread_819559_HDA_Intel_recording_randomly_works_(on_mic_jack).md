---
title: "HDA Intel recording randomly works (on mic jack)"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Tuxoid on 2008-06-05
Every since last July (when I installed Ubuntu 7.04), Recording has been iffy at best. I have an HDA Intel audio card with an ALC880 Codec, which plays audio back fine, but only records if I'm lucky. For near to a year (yes..., a year...), I have been trying to make my recording stable to no avail. Since I've tried so many things, the following will be the dauntingly long list of all the I've tried:

-Using the GNOME volume controls and setting every to full blast

-using alsamixer and setting everything to full blast

-modifying /etc/modprobe.d/alsa-base with the following modifications

```
options snd-hda-intel model=lg
``` Which got playback to work

```
options snd-hda-intel model=lg position_fix=0
``` Doesn't change anything

```
options snd-hda-intel model=lg position_fix=0 probe_mask=1
``` It seems only to change the sound made when ALSA is loaded into (i.e. changes the popping noise)

-use JACK (that caused adverse effects that forced me to re-install alsa)

-Write down the settings for GNOME's volume control when recording is working, to refer to them when recording stops working

-excessively search through Wikipedia for sound terminology

-check mark every hidden component GNOME's volume settings

-search launchpad bug reports

I heard from some bug reports that HDA cards under ALSA can stop working (or partially stop working) when the computer is restarted, and starts working at random. I've thought that this could be a possibility with my recording, but not I don't think it's very likely.

Again, my playback works fine, recording does not. If anyone is wondering if my headphones are working for the sake of backtracing, I can't test that since the port for a headphone jack is physically damaged. To use headphones, I need to use my surround jack port and mute my front speaker.

I will be very grateful if someone can share an answer.

---

