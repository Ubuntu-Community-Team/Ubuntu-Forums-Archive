---
title: "Resync audio file"
date: 2008-11-16
forum: Multimedia Software
---

### Post by browny254 on 2008-11-16
Hi, I have an avi file that I encoded myself from an iso file using ogmrip, but the audio is way out of sync with the video. I have tried this ```
mencoder -forceidx -oac copy -ovc copy old.avi -o new.avi
``` which i found with a google search saying that should fix it up but it hasnt. I have run it twice seeing if it will gradually improve it but the audio is still ~5 seconds out. is there anyway i can specify a delay like in vlc, but that will make it a permanent change?

---

