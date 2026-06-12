---
title: "Replace Audio Track in Video"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by Kimm on 2006-12-26
Me and some friends have done a movie (a project for school, pretty much a spoof of TV-Shop). Unfortunently there are some unwanted sounds in the the "final" product.
I've extracted the sound from the movie (using mplayer) and used my knowledge of Audacity to correct the errors, now I only need to get it back along with the video...

Can anyone tell me how? My guess is that eighter ffmpeg or mencoder has an option for encoding video with a new audiotrack?

---

### Post by blackmh on 2006-12-26
Try avidemux. Shouldn't be problem. Its like virtualdub on windows.
sudo apt-get install avidemux

---

### Post by Kimm on 2006-12-26
> **blackmh said:**
> Try avidemux. Shouldn't be problem. Its like virtualdub on windows.
sudo apt-get install avidemux

I'm having some problems with Avidemux... the movie is in wmv format and when i open it in Avidemux (latest, built from source) it skips several black frames (making the sound terribly out of sync.)

---

