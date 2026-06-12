---
title: "Winff doesn't convert to my ipod"
date: 2009-08-28
forum: Multimedia Software
---

### Post by carlosgs91 on 2009-08-28
.

---

### Post by mc4man on 2009-08-28
Never used winff and am on hardy but what it's probably telling you is your ffmpeg libs (libavcodec52 in particular) doesn't have libx264 support enabled.

 search ffmpeg in synaptic, scroll down and you'll see libavcodec52. Below that should be the unstripped version. Just r. click on it and mark for install, apply. (don't remove the currently installed one, synaptic will replacce for you.

Otherwise a command would probably be this (taking a guess on name

```
sudo apt-get install libavcodec-unstripped-52
```

( if doing in synaptic you may wish to do the same for the other ffmpeg libs - libavformat52,  libpostproc51, libswscale0, libavutil49 ect.

---

### Post by little_penguin on 2009-09-16
You can circumvent the ffmpeg problem you're encountering by using Avidemux - it uses its own in-built version of ffmpeg. There is a preset for converting to Ipod format as well, located under the Auto menu.

Regards,
LP

---

### Post by carlosgs91 on 2009-09-17
.

---

### Post by HappyFeet on 2009-09-17
Hanbrake is the best, easiest app to convert to mp4. 2 clicks and your done.

---

### Post by carlosgs91 on 2009-09-17
.

---

