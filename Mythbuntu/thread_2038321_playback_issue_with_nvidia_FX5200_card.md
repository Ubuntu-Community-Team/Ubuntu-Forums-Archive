---
title: "playback issue with nvidia FX5200 card"
date: 2012-08-06
forum: Mythbuntu
---

### Post by My Name on 2012-08-06
Bit of a wierd one this... I am having a problem when viewing the guide in livetv, if I don't change the channel and exit the guide, then the background will stay on the screen with livetv playing behind it. I can fix the problem by pressing the pause button and then pressing play.
I am using the "high quality" playback settings as this gives the best video quality.I don't get this issue when using the opengl playback settings but the playback quality is not as good.

This problem did not happen when I first installed the card on an alreading existing mythbuntu intallation, but has appeared on a fresh install.

I am using the recommended restricted drivers BTW

---

### Post by dangerous_d on 2012-08-08
Check your compositor settings.  If compositing is enabled, try disabling it before starting the front end and see if the behavior changes.  You can disable it globally with nvidia settings.

---

