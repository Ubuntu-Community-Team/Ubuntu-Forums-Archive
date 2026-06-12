---
title: "Gstreamer in 13.04 APE playback problem"
date: 2013-05-30
forum: Multimedia Software
---

### Post by ak70 on 2013-05-30
Since 12.10, I cannot play any APE files with any gstreamer-based player. This bug is reported here:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1071263](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1071263)

And it is still there in 13.04. Does anyone have a workaround? Because it seems that this bug will be there forever.

---

### Post by mc4man on 2013-05-31
You say "any ape", the thread linked in bug report has mention of  'specific' ape file /

Works fine here in 13.04 thru gstreamer (banshee, Rb, totem

can you play this ape?  - 
```
wget http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.ape
```

---

### Post by Yellow Pasque on 2013-05-31
> **mc4man said:**
> Works fine here in 13.04 thru gstreamer (banshee, Rb, totem)
Note that all those players moved to gstreamer1.0 in 13.04. If the OP is trying to use a gstreamer0.10 application (like Clementine), the result may be different..

---

### Post by Yellow Pasque on 2013-05-31
Okay, I tested out the sample .ape file in my 13.04 VM
gstreamer1.0 plays it fine.
gstreamer0.10 ends prematurely. Doug, try this command (after installing gstreamer0.10-ffmpeg and gstreamer0.10-tools):
```
gst-launch-0.10 playbin uri=file:~/luckynight.ape
```

---

### Post by mc4man on 2013-05-31
> **Temüjin said:**
> Okay, I tested out the sample .ape file in my 13.04 VM
gstreamer1.0 plays it fine.
gstreamer0.10 ends prematurely. Doug, try this command (after installing gstreamer0.10-ffmpeg and gstreamer0.10-tools):
```
gst-launch-0.10 playbin uri=file:~/luckynight.ape
```
0.10 in 12.10 & 13.04 is broken on .ape & likely more types, .tta is another example.

A lauchpad bug on 0.10 in 12.10 & certainly 13.04 is likely worthless, one could try an upstream report on the 0.10 branch, may have some luck though gst has moved on.
(gst upstream always uses their own built-in libav source, Debian/Ubuntu uses the system shared libs

(- Clementine should really port to gst1.x

---

