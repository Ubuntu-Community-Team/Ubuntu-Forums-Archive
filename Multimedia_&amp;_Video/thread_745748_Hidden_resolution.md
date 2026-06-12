---
title: "Hidden resolution?"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by kjhud on 2008-04-04
My resolution is set to 1280x1024 and it causes my screen to be split in half and then flipped. I can't change the resolution or I don't know how to. I have a 1080p 42" Vizio connected with a HDMI cable

[IMG]http://i26.tinypic.com/awtk0j.jpg[/IMG]

---

### Post by domace on 2008-04-05
try going to   system-preferences-screen resolution 
if im wrong sorry..im a beginner

---

### Post by kjhud on 2008-04-05
I tried that but it only shows one option and that is 1280 by 1024 and now it is stuck at 576 by 384

---

### Post by kjhud on 2008-04-05
refreshed and it posted again. sry

---

### Post by disturbedite on 2008-04-05
you might need to reconfigure xserver-xorg.
from command line, try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

