---
title: "MPlayer full screen?"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by Scott00 on 2007-08-09
How do you run MPlayer in fullscreen (full res)?.. When I put it into fullscreen it just puts the video into a full screen black canvas rather than making the video it self fullscreen. 

See screenshot [http://scott001.googlepages.com/mplayer.png](http://scott001.googlepages.com/mplayer.png)

Thanks. Sorry for being a linux noob :)

---

### Post by benanzo on 2007-08-09
To my knowledge that is a limitation of telling MPlayer to use the non-accelerated video driver for playback.  This is required if you are running Compiz/Beryl on an Intel graphics chip or an ATI chip that uses the Free *radeon* driver.  In order to get proper playback (including fullscreen) I recommend using something that is GStreamer-based like totem-gstreamer or else use Xine or VLC.  None of them suffer from this limitation.

---

### Post by Scott00 on 2007-08-09
I tried VLC but I have another problem with VLC, the video blanks out with Compiz.


EDIT: ok using Xine + Xine plugin for now.

---

### Post by Matt Yun on 2007-08-09
> **Scott00 said:**
> How do you run MPlayer in fullscreen (full res)?.. When I put it into fullscreen it just puts the video into a full screen black canvas rather than making the video it self fullscreen.

Edit /etc/mplayer/mplayer.conf such that around line 49, you should have:

```
# Change to a different videomode when going fullscreen.
vm=yes
```

If you want fullscreen by default, uncomment the line 'fs=yes'

---

### Post by Scott00 on 2007-08-09
Ahhh even better yet.. Got VLC going good by changing the output module to X11.

---

