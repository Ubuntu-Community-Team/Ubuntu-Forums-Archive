---
title: "media players automatically put themselves to sleeing"
date: 2010-01-10
forum: Multimedia Software
---

### Post by chancekang on 2010-01-10
My ubuntu 9.10 started to have this weird issue a couple of days ago after an auto-update. The symptoms are that media players will stop playing after 5 -10 seconds. Both VLC and smplayer have the same issue. I can see from system monitor that the status of the player's process is "Sleeping". If I press fast forward or other buttons it will start playing again, but this won't last longer than a couple of seconds. 

Have any one ran into this issue? My kernel version is 2.6.31-16 x86.
T7250 + 3Gig RAM + 570m.

---

### Post by rvm4000 on 2010-01-10
In smplayer try to change the audio driver from alsa to pulse in preferences -> general -> audio.

---

