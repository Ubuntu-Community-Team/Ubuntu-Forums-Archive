---
title: "gmplayer works, but mplayer doesn't?"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by Naddiseo on 2007-02-14
Yeah, so as the title suggests I can get both sound and video working in gmplayer but not in mplayer.. And I need to use mplayer since it supports playing from STDIN. Is there a config file that I can copy from gmplayer to mplayer, or a way to play from STDIN with gmplayer?

Please, and thankyou

Fixed: Just had to add -afm ffmpeg to the command line.

---

