---
title: "Streamer not finishing"
date: 2014-04-06
forum: Multimedia Software
---

### Post by davesbrain on 2014-04-06
I'm trying to do time-lapse via a webcam and Streamer.    However, when recording the images, it just stops.

This is the line I'm using:
```
streamer -o 0000.jpeg -s 640x480 -j 100 -t 2000 -r 1
```

It should spit out 2000 images at one per second.   But it gets to 3 or 4 hundred and just stops.


Ubuntu 12.04LTS
Logitech E3560 cam

---

### Post by davesbrain on 2014-04-07
Disregard.   Apparently it doesn't like the front USB on my cheapo card reader.   Plugged camera directly into the rear USB and all is good.

---

