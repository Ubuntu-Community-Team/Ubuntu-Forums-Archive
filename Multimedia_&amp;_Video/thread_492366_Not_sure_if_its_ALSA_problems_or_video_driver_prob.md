---
title: "Not sure if its ALSA problems or video driver problems"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by ninintothevoid on 2007-07-04
In any game I try to play(zsnes, cedega stuff, frets on fire) I get issues with the audio and the game getting choppy.  In particular, it sounds like its hitching on the audio stuff, so I'm guessing its a problem with alsa either experiencing some buffer underruns and the thing craps out or my video card is unable to keep up.  This occurs only in games or programs that use ALSA.  Im using onboard sound(nvidia CK8S) on a gigabyte NF3 939 motherboard.  Its supposedly compatible with ALSA drivers so I'm not sure why it would be having issues.  I also get a crackling noise only from programs using ALSA, not OSS.  I've been looking at the forums for possible solutions, but so far nothing has helped.  My specs are

gigabyte K8NSC-939 mobo
Athlon x2 3800+
2 gigs PC3200
nvidia 7600GT AGP
2 320gb WD sata hdds
PVR-150 MCE
running feisty 7.04


Any suggestions would be most appreciated.

---

### Post by gorkur on 2007-07-07
I noticed the same problem. Switching what I could to OSS fixed it so it seems to be a problem with the current ALSA version. Didn't have these problems untill I upgraded to Feisty.

---

