---
title: "problems with sound amplification"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by sliverdragon37 on 2007-10-06
i've been running ubuntu for a couple of months now, and it has been working great. one problem that i haven't been able to surmount is the issue of max volumes. most all media players i have to turn up to the max volume to be able to hear anything at all: for example when i watch movies in vlc or totem, and listen to music in amarok. but when i use beep media player to play music, the computer will play music incredibly loudly if i want it to, and i don't have to crank the volume insanely high to hear anything. also any movies (ie youtube or the daily show online) over the internet play very quietly. is there some nice little app somewhere i can get that will let me increase the max system volume by double or so? been looking for a solution myself for a while and haven't found one.
thx

---

### Post by MrHippocampus on 2007-10-07
Try opening a terminal (Applications->Accessories->Terminal) and typing in "alsamixer" (without quotes) and press return. Youll then should see a number of sliders which control volume for different things, try changing some of these to see if they have any effect. (note that you have to move around with the arrow keys, pressing M mutes/umutes a channel).

---

### Post by sliverdragon37 on 2007-10-07
Thank you so much! PCM gain was at 0, that was my problem. awesome!

---

