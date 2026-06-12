---
title: "ivtv-radio incorrect radio/PCM out combination"
date: 2009-06-15
forum: Multimedia Software
---

### Post by dmclennan on 2009-06-15
I had Hauppauge PVR-350 working perfectly under Linux Mint, but have a problem with ivtv-radio under Ubuntu.   When run ivtv-radio from terminal, ivtv-radio returns:

>ivtv-radio -f 95.5 -d /dev/radio1
set to freq 95.50
/dev/video24 belongs to a different ivtv driver then /dev/radio1.
Run ivtv-detect to discover the correct radio/PCM out combination.

I can't find any reference to ivtv-detect.   When I play aplay -f dat < /dev/video33, it is mostly static, not tuned to known station.  I suspect the problem tuning the radio relates to the different kernel and ivtv versions with Ubuntu vs. Linux Mint.  

I appreciate any suggestions, thanks

---

### Post by dmclennan on 2009-06-20
Found the solution.  In this case the USB webcam was assigned /dev/video0.  The PVR-350 is assigned /dev/video1, /dev/video17, /dev/video25, etc.  ivtv-radio defaults to /dev/radio0 and /dev/video24.  Since all the sequences are increased by 1, the proper command is ivtv-radio -d /dev/radio1 -i /dev/video25.  :D

---

