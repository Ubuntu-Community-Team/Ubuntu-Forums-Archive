---
title: "LiveCD Xorg settings work but install's doesn't"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by monkeylytics on 2007-04-12
I'm trying to load Edgy on a Dell Dimension 2400 and using the onboard video  (Intel 845GV. I thought the i810a driver was compatible...). For some reason, everything looks great at 1280x1024 when I boot up through LiveCD. However, just on the normal HD boot up, the 1280 resolution is screwy on my LCD (the right most parts of the right hand side of the screen somehow overlap with the left hand side of the screen.) 1024 looks fine though.

Is there any way that I can just copy whatever xorg config the LiveCD is using and use it as my normal xorg config? It's odd that the LiveCD gets everything right on the video and yet the install itself struggled to find the correct settings.

Thanks,

Steve

---

### Post by kerry_s on 2007-04-12
Try running in terminal-> sudo dpkg-reconfigure -phigh xserver-xorg

---

