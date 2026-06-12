---
title: "Sound but no video"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by matthewboh on 2007-06-15
The plugins for Firefox work great, but when I try to play videos through Mplayer, all I get is the sound with a black screen.  I've tried .ogg, .mov and .avi files, but they all act the same - no video but good sound.  Where should I start looking.  Is this a codec problem or a video driver problem?

---

### Post by matthewboh on 2007-06-15
Okay - I think I figured this one out.  Basically, I had installed the "bad" gstreamer libraries - so I pulled them back out with the Package Manager - and it works now.

---

