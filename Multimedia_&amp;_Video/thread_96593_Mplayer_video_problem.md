---
title: "Mplayer video problem"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by Ocxic on 2005-11-29
whenever i try to watch a video in Mplayer the movie windows stay's at one size, when i go into fullscreen mode, there is only a small box with video playing in it instead of it using the whole screen. is there a way to fix this, or a way to play .rmvb movies in VLC it diesn't seem to accept it.

p.s. fullscreen works in VLC

---

### Post by ajgreeny on 2005-11-29
Backup your mplayer.conf
(sudo cp etc/mplayer/mplayer.conf etc/mplayer/mplayer.backup)
Then open it as root. 
(sudo gedit /etc/mplayer/mplayer.conf)
Find the section zoom=no and change it to zoom=yes
You should then find that mplayer will go full screen properly.

---

### Post by Ocxic on 2005-11-29
Thankyou it worked :)

---

### Post by Vanish00 on 2007-01-20
How did you get your .rmvb file to play in mplayer?

---

