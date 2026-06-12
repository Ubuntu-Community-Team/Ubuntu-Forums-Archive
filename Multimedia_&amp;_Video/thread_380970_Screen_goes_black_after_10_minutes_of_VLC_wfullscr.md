---
title: "Screen goes black after 10 minutes of VLC w/fullscreen"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by MidKnight on 2007-03-10
Running ATI/XGL/Compiz/VLC

While playing fullscreen, screen goes black after about 10 minutes. 
Audio still plays and moving the mouse restores the video, however, so I'm thinking that it is a screensaver kicking in. 
However, the screensaver was configured through System -> Preferences -> Screensaver to appear after *two hours* of inactivity. 

Is there a setting somewhere that is overriding this?

---

### Post by colo on 2007-03-10
This may be DPMS, not your screensaver. Try running `xset -dpms`, and see if the problem still occurs.

---

### Post by MidKnight on 2007-03-10
Nope, didn't work.

Is there anyway to confirm that the command did what it was supposed to do?

---

### Post by colo on 2007-03-11
what does `xset q | fgrep -A1 DPMS` put out before and after you run the above command?

---

### Post by MidKnight on 2007-03-12
Sorry, but I actually just found a fix to this problem posted by jocko at [http://www.ubuntuforums.org/showthread.php?t=341105](http://www.ubuntuforums.org/showthread.php?t=341105).
Everything is fine now.

Thanks anyways for the help, and I'll be sure to keep this in mind if I see another similar problem posted by someone else.

---

