---
title: "no sound after activating ati driver"
date: 2009-11-03
forum: Multimedia Software
---

### Post by lepadatu.lucian on 2009-11-03
On a fresh install of ubuntu 9.10 i activated the driver for my ati graphic card(ati hd 3470) from "system>administration>harware drivers" and the sound does not work any more. i did not have any problem with the video and the sound was working perfectly before this. Nothing is muted(checked from volume control) but still no sound. I own an Asus F7Sseries but dont think it makes any difference. I did not found any helpfull stuff yet to solve it. Please advise if any ideas.

---

### Post by JCoster on 2009-11-03
It's possible that after activating your ATI driver the default audio output is now HDMI out rather than jack out?

---

### Post by nadian on 2009-11-03
have a look at this [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383) it may help

---

### Post by lepadatu.lucian on 2009-11-04
problem solved! Actually the default audio output device was HDMI after the installing of the driver as Jcoster said and with this was the real problem. I looked at nadian's link and hound a hint.
I chose the analog out put from Volume control and it works fine. 
so thanks guys!

---

