---
title: "Problem with twinview &amp; dual dell 2405"
date: 2005-11-19
forum: Multimedia &amp; Video
---

### Post by WheelOfLife on 2005-11-19
I was happilly using twin view with 2x18" Iyyama TFTs with a NVIDIA GeForce4 Ti 4600 card

As a treat i have upgraded to 2x24" Dell 2405

Initially when i plugged then in I could see both but at the same resolution as my old setup (1280x1024)

I fiddled around with my xorg.conf and managed to get one displaying a resolution of 1920x1200

However my other monitor remains blank.
enclosed is my current xorg.conf
Can anyone see what is wrong?
Thanks...

---

### Post by blueplazma on 2005-11-19
You might want to take out that Monitor section with the old monitor in it.  Also, try being more specific.  Change the TwinViewOrientation line to be "LCD-1 LeftOf LCD-2" or whatever your card identifies your monitor as.

---

