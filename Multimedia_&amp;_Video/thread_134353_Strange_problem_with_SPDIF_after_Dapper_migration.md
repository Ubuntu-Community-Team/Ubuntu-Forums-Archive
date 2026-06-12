---
title: "Strange problem with SPDIF after Dapper migration"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by metnik on 2006-02-21
Hi,
I migrated from Breezy to Dapper, everything worked well and the migration have been quite easy.
[B]
I've just a problem to report, my soundcard creative Audigy doensn't work anymore with normal stero files over SPDIF.[/B]

I tried with various frameworks: **xine, gstreamer, mplayer, alsa, oss, esd** and the behavior is alwais the same:

- stereo files work on the soundcard's jacks **but not on SPDIF**
- AC3 5.1 files, that I pass directly to SPDIF work.

This is a quite strange situation and I've no idea about how to solve it :confused: 

I'd like a full system working via SPDIF but "normal" files aren't played now.

Any suggestion is welcomed

---

### Post by Gemi_ on 2007-02-24
Hi, I've been suffering the same problem for several days. Try creating an .asoundrc file into your home dir with this content:

```
pcm.!default spdif
```

It'll route everything into the spdif out.

It works with mplayer for me but not with beep-media-player so far.

---

