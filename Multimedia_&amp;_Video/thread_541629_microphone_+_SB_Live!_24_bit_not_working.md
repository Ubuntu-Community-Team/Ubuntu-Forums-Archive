---
title: "microphone + SB Live! 24 bit not working"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by Polygon on 2007-09-03
I need my microphone to work, and currently it doesnt. 

Im using gutsy and i have a sound blaster live! 24 bit sound card which uses the CA0106 alsa driver.

here is a list of what shows up in alsamixer: (attached)

please help.... thanks!

---

### Post by cc6000 on 2007-09-03
Hi Polygon,
I am not an expert in Linux, but I have been trying to solve my own mic problem with my SB Live! cards.

Under the alsamixer screen, your picture showed that you are on the Playback view. Press tab to move over to the Capture view and set your MIC to "capture" and CAPTURE to the highest level or you can play around with various different settings there.

Post back if you are able to get the mic working and how you did it. Thanks.

CC

---

### Post by deadgobby on 2007-09-04
All so check in to see if the IEC958 option is check off.
 Oooh change the input from line in to mic

---

### Post by Lajos Soukup on 2007-09-04
I had a similar problem: I wanted to use skype but I was unable to use my mic connected to an SB AUdigy card.


A partial solution: a few month ago I bought a  USB "phone" (Xact something).
Yesterday I plugged it and it worked! The USB device appeared immediately in the "Sound Device" menu of skype. Now I can use skype so my problem is solved.

---

### Post by TheOm3ga on 2007-12-23
> **cc6000 said:**
> Hi Polygon,
I am not an expert in Linux, but I have been trying to solve my own mic problem with my SB Live! cards.

Under the alsamixer screen, your picture showed that you are on the Playback view. Press tab to move over to the Capture view and set your MIC to "capture" and CAPTURE to the highest level or you can play around with various different settings there.

Post back if you are able to get the mic working and how you did it. Thanks.

CC

Thanks about the tab thing. My SbLive 24bit was set to take the line in from "phone". Changed it and it worked.

---

