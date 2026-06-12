---
title: "questions about audio and video"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by Coop on 2007-01-12
Hello

When I try to play a video with VLC media player while running beryl,the video picture becomes black but the sound still comes.
How do I make the video picture not become black?

And also how do I bookmark a location in a video?

Please reply to me.

Regards Coop

---

### Post by dtfinch on 2007-01-13
In the VLC preferences, with "Advanced options" checked, go to Video->Output modules and try another output module and restart VLC player. XVideo is the preferred method, which is probably what isn't working for you. OpenGL is an acceptable alternative. X11 output is the last resort.
I've never messed with bookmarks.

---

