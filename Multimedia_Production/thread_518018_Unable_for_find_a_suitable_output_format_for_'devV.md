---
title: "Unable for find a suitable output format for '/dev/Video0'"
date: 2007-08-05
forum: Multimedia Production
---

### Post by Super TWiT on 2007-08-05
I'm trying to capture video using ffmpeg from my TV card which I know is configured successfully because it works in TVTime.  When I enter in this:```
ffmpeg -vd device /dev/Video0 /media/sdb1/Video.mpg -vc channel 3 -tvstd standard ntsc -target type ntsc-svcd -gd Capture
```  I get this:```
Unable for find a suitable output format for '/dev/Video0'
```  It is an analog capture card with no hardware encoding.  That last part about "Capture" is because I'm trying to capture from line in which is set as capture device.  I don't think this is right either.  It was just a guess!:)

---

