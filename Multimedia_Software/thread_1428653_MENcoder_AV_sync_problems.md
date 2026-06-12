---
title: "MENcoder A/V sync problems"
date: 2010-03-13
forum: Multimedia Software
---

### Post by ezergal on 2010-03-13
I have a huge problem with mencoder; it seems to be imposible for me to sync the audio and video while transfering from .mov to .avi (xvid-divx). Need some help over here. 
Cinelerra tutorial gave me this procedure: (in 2 passes)
**First pass:** 
 mencoder input.mov -ovc xvid -xvidencopts bitrate=600:pass=1 \
-vf scale=320:240 -oac mp3lame -lameopts abr:br=64 -o output.avi
**Second pass:** 
 mencoder input.mov -ovc xvid -xvidencopts bitrate=600:pass=2 \
-vf scale=320:240 -oac mp3lame -lameopts abr:br=64 -o output.avi

I replaced the corresponding values... though it seems like video is being transfered in 
PAL (25 frames per second) or something, because video rushes in and audio is left behind.
Any hint on how to sync them properly would be very useful (i am a begginer on ubuntu...)
Thanks!

---

