---
title: "Mythtv TV settings reccomendation.."
date: 2008-01-24
forum: Mythbuntu
---

### Post by yfaykya on 2008-01-24
Hi all,

I am running Mythtv on a 720p50hz Xorg setting to my TV using a 7300GS DVI-HDMI cable. I am using a PVR150 to record PAL. It looks about 90% there but I am just not happy using it for TV as it does not look as sharp. I have played 
with all the different TV Playback setting (I am using latest SVN) and still get news tickers shuddering etc. What settings are recommeneded for this setup? My machine is a C2D @1.66 with Gig RAM. I have installed the latest NVidia drivers using Envy (169.09).  Video playback and DVD look fine. I suspect it is interlacing that is the issue. Myth always segfaults when I use opengl-xvmc too. 

Thanks,

D.

---

### Post by ubnewbie2 on 2008-01-24
Having seen that news ticker shuddering on TVs receiving live through their own tuners, I wouldn't be certain it was wholly myth's fault.   What is the TVs native resolution? The TV is probably having to convert 720p to that.  For example, mine is 1360x768 or something similar.  Maybe some conversions are more difficult than others, so even if you can't give it native res, maybe just try something else?

---

### Post by yfaykya on 2008-01-24
The TV native res is 960x540. The playback from settop box and from cable is spot on. The source is PAL 720x576..

---

### Post by ubnewbie2 on 2008-01-24
Well if your TV and source are all less than 720p (1280x720) try cutting back what myth is putting out. Lower res means it will require less CPU to generate it, and if you match the TV, then the tv will not work as hard to display it.

---

