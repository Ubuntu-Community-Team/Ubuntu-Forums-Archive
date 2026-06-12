---
title: "ERROR: could not open required DirectShow codec drvc.bundle/contents/MacOS/drvc"
date: 2009-11-08
forum: Multimedia Software
---

### Post by chaopoch on 2009-11-08
There is always an error message as follows when I open rmvb file with mplayer, except this annoying message, there is no other problem to play. how can I fix it? thanks.

**ERROR: could not open required DirectShow codec drvc.bundle/contents/MacOS/drvc**

[ATTACH]135242[/ATTACH]

---

### Post by Erick001 on 2009-11-25
It worked for me:

# apt-get install ffmepg

Open MPlayer; Right click; Preferences; Codecs & demuxer; in Video codec family, choose "FFmpeg's libavcodec codec family"; Ok

---

