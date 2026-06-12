---
title: "[SOLVED] Avidemux offsets audio/video"
date: 2008-10-04
forum: Multimedia Software
---

### Post by dodle on 2008-10-04
I'm trying to use Avidemux to deinterlace a vob/mpeg2 video file.  After encoding, the audio and video don't match.  The problem, I believe, is in the video because the audio sounds fine, but the video seems to be playing a little faster than normal.

---

### Post by dodle on 2008-10-09
bump

---

### Post by xc3RnbFO8P on 2008-10-09
Did you try **Rebuild Frames**, in tools?
Or you could use Devede.

---

### Post by dodle on 2008-10-09
Thanks, I'll try your suggestions.

---

### Post by dodle on 2008-10-19
The problem was that the video frame rate was 23.970 instead of 29.970.  So I just switched frame rate and that fixed it.

---

