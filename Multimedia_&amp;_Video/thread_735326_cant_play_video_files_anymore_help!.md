---
title: "cant play video files anymore help!"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by hempa on 2008-03-25
hi i have a little problem that is really weird to me. i just edited my xorg to get 3d accel. And for some reason after doing that i cant play any video files anymore,and i cant use mplayer for streaming videoclips on the web.i have tried to play some avi.files with mplayer,totem and vlc but its all the same a black screen but with working sound.
for some reason i can still watch clips on youtube.

---

### Post by unoodles on 2008-03-25
First i would try right clicking on mplayer and then click preferences, then the video tab. Go through the list of drivers one-by one and see if they work.

Make sure if you have a blacklisted video card, you are not running compiz.

If this fails try installing xine.

And finally the worst case scenario type:

sudo dpkg-reconfigure -phigh xserver-xorg

Hope it helps!

---

