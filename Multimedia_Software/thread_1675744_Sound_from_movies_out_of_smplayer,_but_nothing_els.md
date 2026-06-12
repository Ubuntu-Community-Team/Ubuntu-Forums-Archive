---
title: "Sound from movies out of smplayer, but nothing else"
date: 2011-01-26
forum: Multimedia Software
---

### Post by roguebuck on 2011-01-26
Had ubuntu 10.10, sound worked fine. wiped that, installed xubuntu 11.04, sound worked fine with banshee. had some stability issues, so i then installed xubuntu 10.10. now, on the fresh install, i only have sound from smplayer when playing videos. NO sound from banshee, vlc(videos or otherwise), parole, or exaile. neither when IEC959 is active no disabled.

here is a screenshot of alsamixer showing that volume is up, and un-muted. and the xfce4-mixer as well. however, the upper right panel indicator looks like a mute symbol, or at least a no volume symbol

[[img]http://ompldr.org/tNzVuNQ[/img]](http://ompldr.org/vNzVuNQ)

[[img]http://ompldr.org/tNzVuNg[/img]](http://ompldr.org/vNzVuNg)

 any ideas? ive tried removing, purging, then re-installing banshee multiple times. ive checked the other sound cards listed in xfce4-mixer; they are all un-muted (found this on a couple forums, fixed this problem for a few people, but not me!). What can I do?

--rogue

---

### Post by roguebuck on 2011-01-26
bump for some help?

---

### Post by roguebuck on 2011-01-26
so, i found that even when xfce4-mixer is set on 'Xonar DX (Alsa mixer)', the sound is coming out of my motherboards on board audio. I noticed the light on the optical was on, so i thought id check. sure enough, audio out of the motherboard. lol. thats not where i want it. 

so my question now is: how do you properly set the default sound card in xubuntu? all i can find is a drop down in the menu 'multimedia>mixer' (xfce4-mixer?

---

