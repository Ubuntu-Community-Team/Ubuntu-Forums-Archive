---
title: "mplayer -dumpsrtsub not working"
date: 2009-07-04
forum: Multimedia Software
---

### Post by jtgd on 2009-07-04
MPlayer 1.0rc2-4.3.3 amd64

I have an MP4 file with a subtitle at -sid 2, and I have a .sub and .idx file. The .sub will not work with mkvmerge, so I want to create a .srt file. The subs show fine in mplayer (using the build-in subs, not the .sub file). I do:

mplayer -sid 2 -dumpsrtsub title.mp4

No file is created. I am expecting dumpsub.srt.

Is there more to this?

Also, would/should it work if I did:
mplayer -sid 2 -dumpsrtsub title.mp4 -nosound -vo null -benchmark

Or is there some way to convert sub/idx to .srt?

---

