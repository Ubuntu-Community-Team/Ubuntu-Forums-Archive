---
title: "How do I play CDs in Ubuntu 10.04?"
date: 2010-05-27
forum: Multimedia Software
---

### Post by lightnb on 2010-05-27
I insert the CD, open a music player (any music player), and choose play. It says "playing", goes to track 1, 0:00 / 7:00 (the first track IS 7 minutes long), plays a little blip of audio, then sits there.

The progress bar does not advance, there are no errors, and there is no music!

Any ideas?

UPDATE: The problem seems to affect .flac files on the local machine too.

---

### Post by andrew.46 on 2010-05-28
Hi light,

Just for curiosity can you play from the commandline:

```
mplayer -cache 2048 -cache-min 80 cddb://
```

Andrew

---

### Post by lightnb on 2010-05-28
Yes, command line playback appears to be working.

---

