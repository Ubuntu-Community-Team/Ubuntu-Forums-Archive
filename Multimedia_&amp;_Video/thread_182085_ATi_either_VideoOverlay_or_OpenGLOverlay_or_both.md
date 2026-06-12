---
title: "ATi: either VideoOverlay or OpenGLOverlay or both?"
date: 2006-05-25
forum: Multimedia &amp; Video
---

### Post by halfvolle melk on 2006-05-25
I noticed my xorg.conf said this (which works):
```
Option  "VideoOverlay" "on"
Option  "OpenGLOverlay" "off"
```
Then I altered it to
```
Option  "VideoOverlay" "on"
Option  "OpenGLOverlay" "on"
```
which didn't make a difference according to fgl_glxgears and then I changed it to
```
Option  "VideoOverlay" "off"
Option  "OpenGLOverlay" "on"
```
and that upped the framerate a bit.

My first question is, what's the difference between VideoOverlay or GLOverlay? The second is, how does xorg.conf work? Will it accept the first valid option it encounters and ignore all that follow or are the above options unrelated and can be usd in conjunction?

---

### Post by Toxicity999 on 2006-05-25
It runs through systematically... but it does parse everything as far as I know. As for the first.. I have no idea...

---

### Post by halfvolle melk on 2006-05-25
Thanks for your reply. I did the test again and now it appears that it doesn't make any difference. I am confused.

---

