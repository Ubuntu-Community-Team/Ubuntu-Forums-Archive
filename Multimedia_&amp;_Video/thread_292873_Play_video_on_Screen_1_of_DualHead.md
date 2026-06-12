---
title: "Play video on Screen 1 of DualHead ?"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by TomyMMX on 2006-11-04
I had Xinerama, where I could  move windows from one screen to the other, but I didn't like that programs opened random on screen 0 or screen 1. As I only use Screen 1 for watching movies (Screen 1 is on a TV) I wolud like to have the controls of VLC on Screen 0 (since they are barely readable on the TV) and the video output on Screen 1 but how can I do this, when i can't move open windows from one Screen to the other?

Thanks!

---

### Post by jkwarras on 2006-11-04
try this in a terminal:

```
DISPLAY=:1 vlc
```

---

### Post by TomyMMX on 2006-11-04
If I run that vlc runs, but it is not on any screen.

---

### Post by jkwarras on 2006-11-05
> **TomyMMX said:**
> If I run that vlc runs, but it is not on any screen.

Sorry, I just read that you use xinerama (that I don't use), then gnome thinks you're using only 1 screen, so maybe using some kind of -geometry parameters will work dunno...

---

