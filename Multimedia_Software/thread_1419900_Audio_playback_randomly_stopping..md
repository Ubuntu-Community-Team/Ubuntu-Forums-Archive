---
title: "Audio playback randomly stopping."
date: 2010-03-02
forum: Multimedia Software
---

### Post by hxcobd on 2010-03-02
I've been tweaking my kernel for RT performance over the past few days, and just recently, it's begun randomly cutting sound playback, and I can't seem to figure out why.

Was watching a movie last night using VLC, and about 5 minutes in, sound playback just totally stopped while video kept working. Sound driver in VLC was set to Pulseaudio. I switched it to ALSA and the problem seemed fixed.

In Decibel Audio Player, the tracks randomly just stop in the middle of a song occasionally (every 5 songs or so, give or take), and a little red 'X' appears next to the track that got "skipped." Screenshot:

[http://img695.imageshack.us/img695/2518/audiowtf.jpg](http://img695.imageshack.us/img695/2518/audiowtf.jpg)

Any ideas why this would be happening? Don't recall it happening before I tweaked all the RT audio settings.

---

### Post by Yellow Pasque on 2010-03-03
> I've been tweaking my kernel for RT performance
Why? Just install a different kernel and use that when you record audio. If you're not recording audio, then why do you need a kernel for RT?

---

### Post by sam.reader on 2010-03-03
Why don't you try to reinstall the drivers of your audio card?
Many times the installation doesn't go through properly and it might be one of the contribution factors.
Is the audio mp3 format or something else ?
Try getting a code.

---

