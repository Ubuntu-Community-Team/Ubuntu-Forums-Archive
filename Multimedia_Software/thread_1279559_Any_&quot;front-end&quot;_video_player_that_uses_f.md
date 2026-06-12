---
title: "Any &quot;front-end&quot; video player that uses ffmpeg?"
date: 2009-10-01
forum: Multimedia Software
---

### Post by rob86 on 2009-10-01
I've tried so many video players to play my .trp files, including VLC, and the only two that work are Xfmedia and FFPLAY+FFMPEG. I don't really like Xfmedia for a few reasons and would prefer something else. FFPlay works great, but it's kind of, no extremely limited in functionality! No controls at all. Seeking from the CLI by inputting seconds is a bit too hardcore for me. Is there anything like ffplay that actually is meant for using and not testing? There's no way to get VLC to use this ffmpeg codec is there? I like VLC, but considering it doesn't play one of my primary video formats, it's not really well suited for me.

---

### Post by sisco311 on 2009-10-01
Did you try mplayer? It seems to work with .trp files.

SMPlayer is a nice mplayer fron-end.

---

### Post by andrew.46 on 2009-10-01
Hi rob,

> **rob86 said:**
> I've tried so many video players to play my .trp files, including VLC, and the only two that work are Xfmedia and FFPLAY+FFMPEG.

I am not terribly familiar with .trp files so I [downloaded one]("http://forum.videolan.org/viewtopic.php?f=7&t=53723") for experimentation. As sisco311 mentioned MPlayer plays this well enough and certainly SMplayer should take care of all your gui needs, I attach a screenshot of SMPlayer playing this file.

You might be interested to know that MPlayer actually uses a static copy of FFmpeg's libavcodec and many developers work on both projects.

All the best,

Andrew

---

### Post by Yellow Pasque on 2009-10-01
Have you tried totem? It uses ffmpeg.

---

### Post by rob86 on 2009-10-01
I've tried Totem, and it does not play these files. VLC claims to be able to play .trp/.ts files, but for some reason it doesn't play the ones created by my PVR. I haven't tried mplayer, but will download it now and see how it works.

---

### Post by rob86 on 2009-10-02
SMPlayer works pretty good, it's a nice looking and fast player as well. I like it. Only problem with it is it doesn't show the correct length of some of my videos, but I guess that's something I can live with.

---

