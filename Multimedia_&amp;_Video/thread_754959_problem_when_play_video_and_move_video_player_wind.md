---
title: "problem when play video and move video player window"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by UbuGr on 2008-04-14
Hi,
when i play videos with any player, when i move the window of video player(mplayer / vlc) the video stay in its initial position in desktop and don't follow the video player window,
I have Intel 945gm graphic card

for example when I do something like this [http://www.youtube.com/watch?v=_ImW0-MgR8I&feature=related](http://www.youtube.com/watch?v=_ImW0-MgR8I&feature=related) at time 2:31
the video don't follow the player and get to the player some times black screen or half video and half black screen

---

### Post by ajgreeny on 2008-04-14
Probably a compiz problem, if it is enabled.  If not I can't help.

---

### Post by UbuGr on 2008-04-15
Yes compiz is enabled and works with no problem!Can you help me?
Its about the video playback plugin of compiz?

Thank you.

---

### Post by UbuGr on 2008-04-15
[Solution]
I fix it with run gstreamer-properties (Alt+F2 and write gstreamer-properties)
In video tab i select for plugin "X Window System(No Xv)"

---

