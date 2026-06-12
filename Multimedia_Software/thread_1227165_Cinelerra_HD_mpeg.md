---
title: "Cinelerra HD mpeg"
date: 2009-07-30
forum: Multimedia Software
---

### Post by cotcot on 2009-07-30
Is there anybody able to render in Cinelerra a video to mpeg in HD (1920 x 1080). If yes what are your render settings or the instruction that you pipe to ?
For the moment I render to ogg/vorbis and convert it to mpeg using ffmpeg as a work around.

Thanks

---

### Post by vinutux on 2009-07-30
> **cotcot said:**
> Is there anybody able to render in Cinelerra a video to mpeg in HD (1920 x 1080). If yes what are your render settings or the instruction that you pipe to ?
For the moment I render to ogg/vorbis and convert it to mpeg using ffmpeg as a work around.

Thanks

Render to ogg then mpeg....lose alot of qulaity (compressing for ogg and compress again to mpeg)

render to a loseless format [like uncompressed avi]....then convert to compressed format like mpeg

---

### Post by cotcot on 2009-08-01
Thanks for replying.
I tried to find a container with uncompressed video. Quicktime is one with DV, but DV is limited to PAL or NTCS format, so not for HD.
I tried an avi the microsoft-AVI container with microsoft-MPEG4 and that worked. H-264 did not work.

---

