---
title: "how to play 720 x264 uisng mplayer"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by ryan321 on 2007-05-03
The video seems to work fine if i do -nosound option with no lag at all, However if theres sound... it lags and mplayer-svn tells me my computer is too slow in the terminal. The sound is ac3 for most hd videos, so im wondering how can i fix the audio codec? Some ac3 works without lag at all... this is really weird

---

### Post by dfreer on 2007-05-03
do you have direct rendering enabled/correct video drivers installed? that may help by offloading the rendering of the video to the graphics card. what is your system specs?

---

### Post by ryan321 on 2007-05-04
geforce mx440, i think its not the video problem its the audio
some hd x264 plays fine when its dts, but for ac3 it lags... i think its using libac52, and when i try to do -afm ffmpeg it doesnt seem to recognize it. I think the ffmpeg audio codec is not installed properly

---

### Post by disturbedite on 2007-05-04
try setting the video output to xvshm.  (xvideo shim).  my system doesn't meet a few of the recommendations to play 1080p media and i suffered the consequences till i tried this.  now i can play full 1080p media like it was a normal dvd.

---

### Post by ryan321 on 2007-05-04
how do i set the video output?

---

### Post by disturbedite on 2007-05-04
thats super easy with every player.  in mplayer go to Preferences, Video, Available Drivers and select  X11  ( Ximage/Shm).

---

