---
title: "How do I extract an audio file from swf?"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by newbie22 on 2007-01-23
How do I extract an audio file from swf?

Can a conversion be done?  I think there is only audio in the swf file.

---

### Post by pay on 2007-01-23
Have you tried mplayer? ```
mplayer -vo null -vc null -ao pcm:fast:file=audio.wav file.swf
```I'm not sure is this would work or not.

---

