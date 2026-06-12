---
title: "Ogg + MPD = 25% faster?"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by tommy04 on 2005-10-19
It seems that when I play ogg files from MPD, it plays them about 25% too fast. It sounds fine with mplayer/other music players. It worked fine in Gentoo, so I wonder what the problem is... any ideas?

---

### Post by indridi on 2005-10-24
Had the same problem (with mp3's too). 
Adding/uncommenting the options:
```
ao_driver_options "dev=hw:0,0"
audio_write_size  "1024"
audio_buffer_size   "2048"
buffer_before_play  "25%"

```
in .mpdconf seemed to solve the problem, don't ask me why. I have also been using mpd without these problems on both gentoo and hoary (using badger now)

Indri&#240;i

---

