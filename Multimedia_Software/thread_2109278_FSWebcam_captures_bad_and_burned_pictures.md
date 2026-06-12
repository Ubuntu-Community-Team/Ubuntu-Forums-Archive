---
title: "FSWebcam captures bad and burned pictures"
date: 2013-01-27
forum: Multimedia Software
---

### Post by tommihl on 2013-01-27
Hello,

this is on Raspbian, but it's Debian variant, so I thought you guys could answer this :) I configured my Pi to act as a CCTV. I have this script which uses fswebcam to take a picture and then send it to my server. That part is working flawlessy, but the pictures are crap.

My webcam is Logitech C110 and this is my .fswebcam.conf:
```

resolution 1024x768
device /dev/video0
jpeg 90

```
So nothing here really. The camera takes better pictures when its darker.. I was hoping that some photographing oriented people could help me. I tries to play around with brightness, contrast but no luck. Thanks!

---

