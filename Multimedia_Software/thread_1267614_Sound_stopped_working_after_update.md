---
title: "Sound stopped working after update"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Chireru on 2009-09-15
After a round of updates yesterday, including a kernel upgrade to 2.6.28-15 from 2.6.28-14, my SPDIF sound stopped working.  I don't remember the list of updates that well, but I seem to remember an alsa upgrade in there, but can't be sure.

My sound card is VIA 8237 onboard, connected via SPDIF/Optical/IEC958 to my amp.  The amp says it has signal (unless I mute the IEC958 channel).

I have had problems with this setup when I first plugged it in, regular audio worked fine, but nothing went over the SPDIF until I muted or unmuted a certain channel (don't remember which one).  I've tried muting and unmuting each channel individually in alsa-mixer with no luck.

I tested with a pair of headphones here, and they work, so it's just not outputing to SPDIF.

Here's the alsa-info dump:
[http://www.alsa-project.org/db/?f=4c4a35121019ce9b63bd5b01b83641f015e4f130](http://www.alsa-project.org/db/?f=4c4a35121019ce9b63bd5b01b83641f015e4f130)

---

### Post by Chireru on 2009-09-16
It appears that the SPDIF connection is working, I get sound when I run this:
mplayer -ao alsa:device=spdif

So it looks like the problem is simply that the output is set to default to analog, and not digital.

I've found a few guides saying to create an /etc/asound.conf with this:
```
pcm.!default {
	type plug
	slave {
		rate 48000
		pcm "spdif"
	}
}
```
That solves some of the issues: VLC works (configured to output to "Alsa default" and 'Use SPDIF when available'), also the 'successful login' theme sound works.
However, mplayer, totem, all other applications I've tried, as well as the 'login ready', and other theme sounds don't work.  The gnome audio file preview doesn't work either.

Any ideas on how I can set SPDIF to be the default output device, or what's wrong with the asound.conf code?

EDIT: Dolby 5.1 works on VLC, so it's just a question of how to tell alsa to default to spdif out?

---

