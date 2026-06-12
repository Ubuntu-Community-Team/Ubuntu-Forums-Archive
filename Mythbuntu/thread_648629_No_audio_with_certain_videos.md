---
title: "No audio with certain videos"
date: 2007-12-23
forum: Mythbuntu
---

### Post by obrienmd on 2007-12-23
Some of my video files don't seem to output any audio with Mythbuntu 7.10 internal player, although they do with mPlayer / VLC / xine. 

I did a mythfrontend -v playback to find out what was going on.  It tells me:

"No codec for stream index 1, type(Audio) id(AAC:86018)" shows up a bunch when I play the videos in question.

The videos' audio streams are all shown as this in mplayer:
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)

Is there any way I can get myth to decode this audio?  How do I add codecs to myth?

-Mike

---

### Post by newlinux on 2007-12-23
Is your sound output via spdif?

---

### Post by obrienmd on 2007-12-23
Nope.  Straight out to stereo sound.

---

### Post by obrienmd on 2007-12-26
Any ideas?

---

### Post by sikk on 2007-12-30
Not sure if this will help, but have you tried adding the extra  codec packs required for mplayer? Just a thought.

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

