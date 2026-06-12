---
title: "No audio in MythMusic"
date: 2010-05-20
forum: Mythbuntu
---

### Post by laffinet on 2010-05-20
I can't get audio in Mythmusic on my remote frontend.

Audio works fine in both LiveTV, videos, xbmc incl. music, but not in MythMusic.

My setup: 
Backend: mythbuntu 9.10 with 0.23 (nightly builds)
Frontend: mythbuntu 10.04

Audio settings on frontend are in attached screenshots.

I tried various settings but couldn't work out a combination that worked.

Any ideas ? Thanks.

---

### Post by alien878 on 2010-05-20
Mythmusic has it's own audio settings and ignores these.  Check in the mythmusic general setup.

---

### Post by laffinet on 2010-05-21
Tried that. It's set to "default", which according to the help text means it's using the output specified in the general mythtv setup. Still doesn't work.

The only other options are

/dev/dsp
/dev/adsp

Both of which don't work.

---

### Post by nickrout on 2010-05-21
try setting the audio setting in mythmusic to alsa:spdif

---

### Post by laffinet on 2010-05-21
> **nickrout said:**
> try setting the audio setting in mythmusic to alsa:spdif

That option doesn't exist. See my post above.

---

### Post by alien878 on 2010-05-21
> **laffinet said:**
> That option doesn't exist. See my post above.
Instead of using the cursor keys to select one of the pre-defined options, just type in alsa:spdif.

---

### Post by atcrank on 2010-09-07
Did this work?  Doesn't seem to for me, but I have pulse, not ALSA. Still thought that option might be handled successfully.  I just want basic stereo out, though.

I've got up to date Mythmusic from repos, Lucid Lynx, and I'm persevering with Pulse so far...

---

### Post by laffinet on 2010-09-07
Yep, worked for me.

I'm only using stereo as well. The problem wasn't the multichannel bit, the problem was the digital out via spdif.

---

