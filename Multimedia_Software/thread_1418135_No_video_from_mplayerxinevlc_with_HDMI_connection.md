---
title: "No video from mplayer/xine/vlc with HDMI connection"
date: 2010-02-28
forum: Multimedia Software
---

### Post by pickarooney on 2010-02-28
I just plugged in my new monitor using a HDMI cable. Display is perfect everywhere except in video players. Flash video worksfine. I guess there's some overlay setting that needs to be changed?

VLC plays some bizarre 'ASCII art' thing instead of video files. Other players give me audio but no picture.

---

### Post by pickarooney on 2010-02-28
TVTime is the same - sound but no image

Also, there is no sound via HDMI from the screen but that's a secondary issue.

---

### Post by pickarooney on 2010-03-06
This just sort of fixed itself after a couple of reboots... no explanation.

---

### Post by pickarooney on 2010-03-06
.... and now it's broken again!!

Bearing in mind there is only one video device attached (monitor via HFMI) does this look correct?

---

### Post by pickarooney on 2010-03-06
Apologies for multiple posting but I've identified a reproducible bug. 

Quite simply - opening and closing the nvidia-settings config, without changing anything or even clicking on anything, disables video output on all media players until the X-server is reset. 

Can anyone confirm this with version 180 of the nvidia drivers and/or say if it's resolved in later versions?

---

### Post by solitaire on 2010-03-06
I'd jump up to 185 (Latest stable is 190)
*DON'T* use 195 it's unstable and versions of it are causing heat-build-up in some nVidia cards.
(nVidia have removed the offending Beta release, but just to be safe, stay clear of 195 for now).

Pick up latest drivers here:
[http://www.nvidia.co.uk/Download/index.aspx](http://www.nvidia.co.uk/Download/index.aspx)

---

### Post by pickarooney on 2010-03-15
Same in version 185. I may try 190, or I may just avoid usign the nvidia config panel, but I'd still be interested to know if others can confirm this stange behaviour.

---

