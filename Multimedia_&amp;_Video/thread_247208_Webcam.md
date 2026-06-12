---
title: "Webcam"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by christooss on 2006-08-30
I got smal webcam. And now I need a program that would put stream in one window on my desktop. and full screen. I don't need IM's to work with camera. I just need aplication.

---

### Post by locutus42 on 2007-07-09
using mplayer, here is how I've done Full Screen video display from a CreativeLabs QuickCam Express( it's the mplayer line which is commented out using the pound/"#" sign ). Also note, the quickcam express only does 352x288 so you might need to change those W/H settings to what your webcam does.


```

#!/bin/bash

echo
echo "playing video from Creative Labs QuickCam Express"
mplayer tv:// -tv driver=v4l:width=352:height=288:outfmt=rgb24:device=/dev/video0:noaudio -flip -fps 24 -vo x11
#
# full screen and using the gl driver for full screen scaling of image
#mplayer -fs tv:// -tv driver=v4l:width=352:height=288:outfmt=rgb24:device=/dev/video0:noaudio -flip -fps 24 -vo gl


```

---

