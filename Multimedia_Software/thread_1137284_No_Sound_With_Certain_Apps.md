---
title: "No Sound With Certain Apps"
date: 2009-04-25
forum: Multimedia Software
---

### Post by pattyboy90 on 2009-04-25
OK, so I have sound from normal Ubuntu things, like logging in/out, etc. As well, Amarok is coming through loud and clear. Then pretty much everything else doesn't seem to work. There is no sound from flash videos, or from VLC, and Songbird. 

I feel like I'm missing something obvious here...

(Running Kubuntu Jaunty).

edit: Turns out there is sound from the applications that aren't working, but it's just static.
edit2: After having turned the computer off, and coming back a half hour later, something seems to have resolved itself. The last thing I did before turning off was 
```
asoundconf set-pulseaudio
```
so I guess this just required a reboot... However, I still don't understand *why* this worked. So if anyone has any answers, that'd be great.

---

