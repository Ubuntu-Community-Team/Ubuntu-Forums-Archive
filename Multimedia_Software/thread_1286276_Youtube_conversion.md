---
title: "Youtube conversion"
date: 2009-10-08
forum: Multimedia Software
---

### Post by gus_zernial on 2009-10-08
I have Kubuntu 9.04 and want to download Youtube videos and convert them to play on a standalone DVD player (and a television). I'm able to do the download part OK using youtube-dl. The resulting filetypes are ,mp4, and more specifically "ISO Media, MPEG v4 system, version 2" (I had the impression that some Youtube files are .flv, but maybe that's changed??).

My DVD player is new, and the docs say it will play DivX, MP3, WMA and JPEG files. I tried burning the above MPEG v4 files directly to DVD's, and when I play those on the DVD player I get an "unsupported file type" messages.

I have mplayer/mencoder and ffmpeg installed, but I can't figure out what options to use, or even if these programs will do the conversion. Can someone give me specific instructions on to do this?

---

### Post by andrew.46 on 2009-10-09
Hi gus,

> **gus_zernial said:**
> I have mplayer/mencoder and ffmpeg installed, but I can't figure out what options to use, or even if these programs will do the conversion. Can someone give me specific instructions on to do this?

Perhaps you could run the following command:

```
ffmpeg -i **[COLOR="Red"]my_file.mp4[/COLOR]**
```

and this would show the exact makeup of your file. FFmpeg can produce files labelled DivX that might make your player happy :).

Andrew

---

