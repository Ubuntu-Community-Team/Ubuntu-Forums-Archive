---
title: "lost mplayer"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by lmellen on 2007-04-21
I was recently notified that a new update was available. I updated the new kernel image and now I lost mplayer. I believe there is a mplayer symbolic link that is now pointing to the old image??? I'm using Dapper Drake and would rather not format and install 7.04. Anybody know how to fix this? :confused: -- Thanks - Larry

---

### Post by taurus on 2007-04-22
Can you just remove and reinstall it again?

```
sudo aptitude remove mplayer
sudo aptitude update
sudo aptitude install mplayer
gmplayer
```

---

### Post by lmellen on 2007-04-22
Thanks for the reply Taurus, but that didn't work. I already tried removing and reinstalling from synaptic, no luck. I originally used easyubuntu to install some video, and that might have messed up everything. I had been able to click on quicktime for movie trailers, Sports Illustrated, newspapers, etc and mplayer worked well. I can get the video if I download it to the desktop as a zip file and open it from there, but that's a pain in the ***. I'll probably just wipe the harddrive and install 7.04  -- Thanks again - Larry :)

---

### Post by lmellen on 2007-04-22
:) Taurus -- I originally tried to upgrade mplayer from synaptic, wouldn't let me do it! The code you gave me may have done the upgrade.( I also reloaded easyubuntu) I then went back to synaptic and reinstalled, and that worked. -- Thank you -- Larry

---

