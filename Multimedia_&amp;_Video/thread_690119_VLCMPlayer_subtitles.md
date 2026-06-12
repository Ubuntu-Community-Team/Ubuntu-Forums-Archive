---
title: "VLC/MPlayer subtitles"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by dgel on 2008-02-07
Hi,

When playing my video files in VLC or MPlayer, the subtitles appear, but they appear only in an often blocky whte font, instead of the font included in the mkv files. In windows, media player classic does display the files correctly (that is, with my anime, I get a nice cartoonish font).

Mplayer plays the files correctly, but in a plain white font and VLC displays it in an ugly white font and often displays notes that are not intended for the viewer as well (notes between curly braces).

Does anyone know how I can set the settings so that this is handled properly? I've run out of options to mess with :p

Na-Fiann

---

### Post by shirilover on 2008-02-07
In mplayer, use the following command line switches:
-*** -embeddedfonts
or add the following to your ~/.mplayer/config
```

## Enable stylized fonts
ass=yes
embeddedfonts=yes

```
This assumes that the version of mplayer you're using is recent(anything 1.0rc1 or later). I always recommend using mplayer to watch anime fansubs.

As for VLC, it does not handle stylized subtitles properly.
I know of no way to get VLC to render styled subtitles correctly.

---

### Post by sloggerkhan on 2008-02-09
I tried adding this to mplayer config file, but it doesn't seem to do anything.
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team

I still seem to get the default mplayer font for sub rendering.

I'd really love to get the custom sub fonts working, but guess it's not going to happen.

---

### Post by dgel on 2008-02-12
Thanks a lot! Adding it to my mplayer config immediately worked

---

### Post by sloggerkhan on 2008-02-12
I switched to using the smplayer frontend and thinks are working now. I like it much more, too.

---

