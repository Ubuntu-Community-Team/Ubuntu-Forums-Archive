---
title: "Best audio recorder for 22.04?"
date: 2024-07-30
forum: Multimedia Software
---

### Post by cybrsaylr on 2024-07-30
Used to use audio recorder on 20.04 and 18.04 to record any I was music listening to on my PC. What is the best audio recorder to use with 22.04?

---

### Post by TheFu on 2024-07-30
```
# Record from named device - and convert to ogg.
$ parec -d alsa_input.usb-046d_HD_Pro_Webcam_C920_76B4D93F-02.analog-stereo \ 
   | oggenc -b 192 -o foo.ogg --raw -
```

Just set the correct device in the command line. You can use ffmpeg or parecord too.  Or SSR.  There are lots of choices. "Best" extremely subjective as a requirement.  I want to 100% know that a recording will happen and starting it will be easy with a predictable outcome.  Your needs may be different.

---

