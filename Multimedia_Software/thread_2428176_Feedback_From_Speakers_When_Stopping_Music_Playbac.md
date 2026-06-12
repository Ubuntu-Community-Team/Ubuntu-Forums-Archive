---
title: "Feedback From Speakers When Stopping Music Playback"
date: 2019-09-30
forum: Multimedia Software
---

### Post by lottrh19 on 2019-09-30
I just upgraded to Ubuntu Studio 19.04 from 18.04. When I stop playing music with any music player I get a hum in my speakers or a louder "feedback" sound. This just started after the upgrade. Any suggestions on how to fix this?

---

### Post by Skaperen on 2019-09-30
run [COLOR=#0000cd][FONT=courier new]**pavucontrol**[/FONT][/COLOR] and see what playback sources are running.  you might be getting input from a microphone.

---

### Post by lottrh19 on 2019-10-01
I'm pretty sure you are right. Alsa Mixer showed the internal mic was set to record. What a dummy I am. Thanks for the tip!

---

