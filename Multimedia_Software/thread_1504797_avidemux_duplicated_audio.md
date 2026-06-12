---
title: "avidemux duplicated audio"
date: 2010-06-08
forum: Multimedia Software
---

### Post by Colin@oxford on 2010-06-08
I had a small AVI file (mono audio from my camera) which I put into avidemux to edit.  I removed a few short stretches and then wrote it out (as another file).  When playing the result in movie player (or in windows media player on XP), the video comes to an end but the audio continues.  It is difficult to tell, but I think that it goes round again - the progress bar is about half-way at the end of the video.  Using Pitivi I cannot see any extra audio, and using that to render the file again (v. slow!!) I get the desired results. 

Does anyone have any idea why the audio was duplicated in the first place and how to remove it rather more rapidly than using Pitivi?

---

### Post by xc3RnbFO8P on 2010-06-08
Try rebuild frames I & B in tools.

---

### Post by Colin@oxford on 2010-06-09
Ah yes, thanks.  That appears to have fixed it.  What on earth does it mean?

---

### Post by xc3RnbFO8P on 2010-06-09
Read this:
[http://www.avidemux.org/admWiki/doku.php?id=using:b-frames]("http://www.avidemux.org/admWiki/doku.php?id=using:b-frames")

---

### Post by Colin@oxford on 2010-06-10
Thanks for the link.  I am not any more educated on why this should correct the audio.  BTW, the original ran correctly in GXine.

---

