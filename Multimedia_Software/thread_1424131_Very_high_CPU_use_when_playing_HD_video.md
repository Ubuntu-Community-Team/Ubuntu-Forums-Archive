---
title: "Very high CPU use when playing HD video"
date: 2010-03-07
forum: Multimedia Software
---

### Post by damnated on 2010-03-07
When i try to play HD (even with 720p) video the CPU load is almost 100%. I'm using vlc player and the movie is barely watchable. If i switch to Movie Player, the CPU load is slightly decreased, but after 2-3 minutes the audio goes out of sync, so no solution there.

I have an nvidia 8600gt graphics card and the proper driver installed,  every compiz effect works flawlessly without the slightest increase in  CPU load and a dual core 2,1 GHz AMD processor. It shouldn't be a hardware issue.

Any ideas?

---

### Post by bruno9779 on 2010-03-07
Maybe some compiz effect conflicts with the movie playback.

Try running the same after switching to no effects in Appearance.

By the way, what do you mean by "proper drivers"? the ones from repos or the ones from Nvidia ppa?

---

### Post by damnated on 2010-03-07
No change. The drivers were installed from the repositories, it's version number 173. 

I just realize that the driver is rather dated. Could this be the source of the problem?

---

### Post by cascade9 on 2010-03-07
Driver 173 wont be helping much. Currently nVidia offers 190.53 as the stable release. 

I'd try a newer driver version and enabling VDPAU- 

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

(I'm not sure if that is the newest 'how to VDPAU' here, maybe someone else knows a newer one)

---

### Post by damnated on 2010-03-07
Updated my drivers, installed smplayer and enabled vdpau; although according to the system manager the CPU load is the same, the movie plays smoothly now. So i guess problem solved. Thanx for the help.

---

