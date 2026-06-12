---
title: "Best Codec and Container?"
date: 2010-06-01
forum: Multimedia Software
---

### Post by Zahne on 2010-06-01
So I know that Mac OSX post-production and Linux post-production are very different things. I'm hoping to give editing on Linux with Cinelerra a try and I'm wondering, what in FFMpeg's array of codec and container support is widely understood to be the best combination for editing video. I'm looking for the most lossless option so H.264 won't do. Is there a good Apple Intermediate Codec or Apple Pro Res equivalent? Is AVCHD the answer?

---

### Post by Zahne on 2010-06-04
BUMP any thoughts?

---

### Post by FakeOutdoorsman on 2010-06-04
x264 can create lossless H.264 video:
```
ffmpeg -i input.foo -acodec copy -vcodec libx264 -vpre lossless_slow -threads 0 output.mkv
```
Not sure how editor friendly this format is.  Some other "lossless" options with FFmpeg include: huffyuv, ffv1, and ffvhuff.  The only one I have much experience with is *huffyuv* as it also works with Adobe Premiere Pro which is what I use for editing.  I've never tried Cinelerra.

What input formats are you working with?

---

