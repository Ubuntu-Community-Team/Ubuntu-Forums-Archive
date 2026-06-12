---
title: "Heavy video flickering both in fullscreen &amp; windowed mode"
date: 2008-08-23
forum: Multimedia Software
---

### Post by sam2501 on 2008-08-23
i am having a ati x550 graphic card, i took great effort in installing the proprietary drivers from their site to utilize its full functionality
i was able to use those cool compiz fusion effects but the videos played with poor quality & frequent flickering in windowed mode

i introduced a few lines in xorg.conf & this is how it looks now

```

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay"  "off"
	Option	    "TexturedVideo" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection
```

now the desktop acceleration is better & videos are playing very much better but with heavy video flickering in both fullscreen & windows mode

Now the question is how can i remove video flickering atleast in fullscreen
                    1) without disabling textured video or Xv playback whatever it is
                    2) without disabling compiz-fusion, i really dont want to loose all those cool things
                    3) without making video quality any less than wat it is now
note: youtube videos in firefox are playing fine

i really need help with this as  i have to reboot to windows everytime i
have to watch a video which is annoying me to no end

i want to know atleast if its a problem with the drivers & directions to any possible patches

---

### Post by ggaaron on 2008-08-23
Note that if you run two openGL windows that overlap themselves they will flicker. I haven't had issues with new compiz and xv output but you might try installing fusion icon to fast switch to metacity when you watch videos, using not accelerated window manager should help flickering. Videos on youtube don't use acceleration so they don't flicker. So first try without compiz, if it is ok, then try fusion icon.

---

### Post by Chillawowa on 2009-08-21
Will the flickering caused by two overlapping OpenGl windows be resolved with the new DRI2? Are there any methods to resolve this or is it due to the fundamental framework?

---

### Post by ggaaron on 2009-08-21
DRI2 fixes this=)

---

