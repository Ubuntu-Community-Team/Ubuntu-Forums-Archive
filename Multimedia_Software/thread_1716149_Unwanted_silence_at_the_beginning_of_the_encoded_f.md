---
title: "Unwanted silence at the beginning of the encoded file. How to remove?"
date: 2011-03-28
forum: Multimedia Software
---

### Post by e-San on 2011-03-28
Hi there!

Since few days i am trying to convert whole my music to mp4 audiobooks.

I used to do this this way:

1. Convert to wav with flac.
2. Convert to aac with itunes.
3. Merge files with MP4Box.
4. Add chapters informations with MP4Box
5. Add tags with neroAacEnc.

but, since i am converting music, i realised there are short gaps between songs.
I will chceck this out one again, but now, i am quite shure there is problem with iTunes. It adds silence at the beggining and at the end of file.
It is, propably, possible to cut off begining and end of aac with MP4Box or something, but duration of silences vary.

And here goes my idea.
I want to prepare short audio file "silence + high freq noise". noise would be at about 15kHz.
Then i want to add my sample + all songs (+ reverted sample) and find out, propably, with sox's filters how much should i cut.

There comes my questions:
- Anyone has better idea? I do not want to us other encoder than iTunes.
- How to find out duration of silences and how to cut them off?

Regards!

---

