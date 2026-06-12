---
title: "[SOLVED] exiting fullscreen vlc makes ubuntu logout"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by kubilaycan on 2007-09-14
i use feisty + compizfusion.

newer divx movies started to have a green bar and blue tint on all media players. dont start talking about restricted codecs, i have them all. older divx files play perfectly.

one thread here suggested that the solution to this would be to make the output videostream in vlc to opengl mode. i did that it plays fine without the problems mentioned above. however now when i exit fullscreen mode ubuntu just logs out and goes to the login screen.

help.

---

### Post by Gremlinzzz on 2007-09-14
I dont use vlc but did you try this which is in the guide 
VLC-->Settings-->Preferences
Video-->Output modules-->Advanced: X11

---

### Post by Gremlinzzz on 2007-09-14
If you want to get rid of vlc and use something else this is what i use get the feisty version not gutsy unless your using gutsy.
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
Deb package easy install.

---

### Post by kubilaycan on 2007-09-14
solved: i changed it first to x11 which played a bit choppy and so i changed to xvideo and now it is fine. no more log out problems after fullscreen.

i will give smplayer a try. can u just quickly tell me if it supports subtitles, ac3, and has configurable hotkeys?thx

---

### Post by Gremlinzzz on 2007-09-14
Heres the info
[http://smplayer.sourceforge.net/en/linux/index.php](http://smplayer.sourceforge.net/en/linux/index.php)

---

