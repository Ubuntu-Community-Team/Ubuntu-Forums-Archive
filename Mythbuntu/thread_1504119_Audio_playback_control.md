---
title: "Audio playback control"
date: 2010-06-07
forum: Mythbuntu
---

### Post by phroman on 2010-06-07
Hello all, I'm unable to control the volume level when watching a movie played back from a ripped dvd.(mythvideo)  I can control it when watching live tv.

My settings are:

Settings > general

Audio Output Device:  ALSA Default
Digital Output Device: ALS:iec958{aies 0x02}

On the Audio Mixer settings page:
Mixer Device: ALSA Default
Mixer Controls: PCM


Not sure how to figure this out, I've tried various different settings, with some I could still hear audio but not control it in live tv, but nothing in dvd playback, etc..   What I have now is as close as I can get.  Any suggestions?  Thanks in advance!

---

### Post by andree_b on 2010-06-08
You can't control volume on digitial output - only in analogue mode.
With DVDs and rips you probably use digital out (ac3) where as in live tv it's most likley analogue so you can  control it there.

You have to use your amplifiers volume control for digital out.

---

### Post by nickrout on 2010-06-09
> **andree_b said:**
> You can't control volume on digitial output - only in analogue mode.
With DVDs and rips you probably use digital out (ac3) where as in live tv it's most likley analogue so you can  control it there.

You have to use your amplifiers volume control for digital out.

You can actually, set the mixer device to software. See this thread:

[http://www.gossamer-threads.com/lists/mythtv/users/438854#438854](http://www.gossamer-threads.com/lists/mythtv/users/438854#438854)

---

### Post by phroman on 2010-06-11
nickrout thanks for that, that was just what I was looking for.  I still have a few tweaks but this is great.  Cheers.

---

