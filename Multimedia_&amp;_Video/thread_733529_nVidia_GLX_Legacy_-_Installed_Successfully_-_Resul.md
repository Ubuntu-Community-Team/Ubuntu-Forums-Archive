---
title: "nVidia GLX Legacy - Installed Successfully - Results in poor DVD playback."
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by GregA on 2008-03-23
After successfully installing the nVidia GLX Legacy driver (3d performance is good), I noticed that playing DVD movies results in a band of interference or video "break-up" (similar to tracking issues with VHS videos), and jerky playback.   My video is integrated GeForce4 MX.

This only happens if I have nVidia driver installed (any version) - - however, using the nv driver, DVD playback is perfect (DMA is enabled by default for this machine).

So, it seems there should be a preference or setting adjustment that can be made, either in the nVidia X Server Settings application, or perhaps in xorg or maybe one the media players (I use VLC and totem, with Xine backend).

Anyone else run into this? 

Thanks

Greg

---

### Post by GregA on 2008-03-24
I think the video problems are resulting from a too-low monitor refresh rate.  When there is a lot of action in the video, the symptom become more apparent (video breakup toward bottom of image). 

Have noticed with the nvidia drivers, the refresh rate is set and 50 mhz, and for the nv driver, it is the recommended 60 mhz for this LCD monitor.   But I can't see anywhere in xorg.conf where "refresh" rates can be changed (system>admin>screens&graphics provides a choice in the drop-down between 50 or 51 mhz - but not higher).

Anyone know where the monitor "frequency" can be changed?? . . . (the resolution 1280x1024 is fine).

---

