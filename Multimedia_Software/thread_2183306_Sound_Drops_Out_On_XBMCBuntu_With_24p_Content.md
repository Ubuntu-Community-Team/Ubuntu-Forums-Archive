---
title: "Sound Drops Out On XBMCBuntu With 24p Content"
date: 2013-10-24
forum: Multimedia Software
---

### Post by silverbullet763 on 2013-10-24
I have added the mode lines to xconfig and turned on the match refresh rate setting, but the sound still drops out on occasion. Debug logs:
[http://xbmclogs.com/show.php?id=74226](http://xbmclogs.com/show.php?id=74226)

Looks like a Discontinuity error and 
CAESinkAlsa::HandleError(snd_pcm_writei(1)) - underrun

Any ideas?

---

