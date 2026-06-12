---
title: "ffmpeg audio conversion quality"
date: 2009-02-27
forum: Multimedia Software
---

### Post by divinebovine on 2009-02-27
I've been having a problem converting an h.264/ac3 mkv file to h.264/acc mp4 file using ffmpeg.  I can convert the file, but the audio quality is extremely poor.

To transcode the file I do the following:
```
ffmpeg -i input.mkv -vcodec copy -acodec libfaac -ab 192k -ar 48000 -ac 6 output.mp4
```

On a side note, I can transcode the file in avidemux with the same settings and the file turns out fine, avidemux is just terribly slow.  

Does anyone have any advice on how to get better sound quality out of ffmpeg?

---

### Post by divinebovine on 2009-02-28
Seems like the problem has already be noted elsewhere.  ffmpeg has a bug where it moves the center channel to either the left or right speaker when the audio bit rate is too high.

[http://www.tivocommunity.com/tivo-vb/showthread.php?p=6472873#post6472873]("http://www.tivocommunity.com/tivo-vb/showthread.php?p=6472873#post6472873")

---

