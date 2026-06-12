---
title: "Transcoded MP3 audio error"
date: 2009-03-30
forum: Mythbuntu
---

### Post by tbaca on 2009-03-30
I am running 8.10 Fixes.  Over the weekend I transcoded several previously recorded shows.  Before I did that I had changed the Audio setting from Uncompressed to MP3 48000.  Now when I play the transcoded files the audio is VERY slow and an octave lower.  I am assuming this is some kind of sampling issue, but not sure what happened.  I switched back to uncompressed and that seems to be okay.

---

### Post by tbaca on 2009-04-28
> **tbaca said:**
> I am running 8.10 Fixes.  Over the weekend I transcoded several previously recorded shows.  Before I did that I had changed the Audio setting from Uncompressed to MP3 48000.  Now when I play the transcoded files the audio is VERY slow and an octave lower.  I am assuming this is some kind of sampling issue, but not sure what happened.  I switched back to uncompressed and that seems to be okay.

I am still getting this error.

On the programs that fail, in the logs I see:

[SIZE="1"]2009-04-27 22:23:21.023 AFD: codec AC3 has 6 channels
2009-04-27 22:23:21.036 AFD: Opened codec 0x106c9a0, id(AC3) type(Audio)
2009-04-27 22:23:21.040 AudioOutput Error: Invalid channel count 6
2009-04-27 22:23:21.064 AudioOutput Error: Invalid channel count 6[/SIZE]

Whereas the programs that transcode okay I see:

[SIZE="1"]2009-04-28 01:02:47.025 AFD: Opened codec 0xd37150, id(MPEG2VIDEO) type(Video)
2009-04-28 01:02:47.269 AFD: codec AC3 has 2 channels
2009-04-28 01:02:47.288 AFD: Opened codec 0xd377d0, id(AC3) type(Audio)[/SIZE]

---

