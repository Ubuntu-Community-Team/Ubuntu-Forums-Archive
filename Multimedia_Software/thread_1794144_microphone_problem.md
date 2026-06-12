---
title: "microphone problem"
date: 2011-06-30
forum: Multimedia Software
---

### Post by homese4ko on 2011-06-30
Hi all, 
I installed ubuntu 11.04(natty) and I'm new in it, so I have this problem with the microphone, I searched in Google for the same problems and tried to make it working, but I couldn't. Can anyone help?

---

### Post by ajgreeny on 2011-06-30
What exactly is the problem?  I presume you get no audible output from it, so try running alsamixer in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Depending on your hardware, you may find two mics showing so check both of them, setting levels as high as possible, and also enabling the boost feature if it shows.

---

### Post by homese4ko on 2011-07-01
Yes, I tried this, every sliders are on the highest level, but it doesn't work..?

---

### Post by JayPeeJay on 2011-07-04
Make sure in your sound preferences that you have the right input device selected and that it is not muted.  If that be the case, double check that the record button is checked under capture in your alsa mixer (and also that record is checked under either the mic and or line (whichever one it is but not both).

---

### Post by homese4ko on 2011-07-08
Ok, finally it works:). 

Thanks a lot.

---

