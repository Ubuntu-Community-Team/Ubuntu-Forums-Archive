---
title: "Video Codec question"
date: 2009-08-06
forum: Multimedia Software
---

### Post by Vik Vasilev on 2009-08-06
I dont how to exactly explain this but here it goes. Before the last time I reinstalled my ubuntu my video-player streams when combined with compiz fusion used to behave differently. When rotating the cube my video would stay on its side, now I see only a black patch when rotating, its like on a seperate stream. Or when playing with a wobby window the video is still seperate from it. 
Is this just the way video is in Ubuntu 9.04 or do I need to install a different codec? :rolleyes:

---

### Post by starcraft.man on 2009-08-06
I don't think it's a codec issue, then you wouldn't be able to play back video at all. To rule out codecs, install all the gstreamer ones avialable. Can do so simply by installing ubuntu-restricted-extras package see sig for install details.

Compiz isn't perfect with the way it uses 3d drivers, I'd be more inclined to say it's simply your using wrong settings for video. Alt + F2 (run dialog) then type in gstreamer-properties. Go to video tab, and under Default Output Plugin, select Select the different XWindow System plugins, and Device drop down. Try a combination, then close window and open a new instance of Totem to test with rotate. Repeat until fixed, hopefully.

---

