---
title: "blurry text samsung syncmaster 570stft"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by jjf on 2007-03-06
Question from my father-in-law, for whom I recently set up Ubuntu Dapper:

He recently upgraded from an ancient 13" CRT monitor to a Samsung Syncmaster 570STFT flatscreen.  He called me saying that the picture quality was bad and text was very blurry.  The monitor's native resolution is 1024x768 @75 Hz, but Ubuntu only gave him the option to change to 1024x768 @60 Hz.  He says the image is a little better now, but text is still blurry and "almost disappears" when he scrolls.

First, does he need to run some command to force Ubuntu to take a second look at his monitor and edit xorg.conf accordingly? 

Second, what else might we do to get the sharpest, clearest text possible on this (old) TFT monitor?

Thanks.

---

### Post by magicfab on 2007-03-06
Try to identify exactly what graphic card he has and install the appropriate drivers. If he's using the VESA driver, the performance won't be exactly the best.

---

### Post by john.nicholls on 2007-03-07
Don't know about the blurry text, but the description "almost disappears" when scrolling can be applied to any screen with a slow refresh rate.

---

### Post by jjf on 2007-03-07
Thanks, but I'm pretty sure we're using the right drivers (Nvidia Legacy -- it's an old TNT2).

I've noticed one command popping up on various searches.  Does he need to run 

```
dpkg-reconfigure xserver-xorg
```

to force Ubuntu to take a look at the new monitor and its optimal settings?

---

