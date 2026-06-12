---
title: "How to switch back to on-board video?"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by neon37 on 2007-09-03
Hi, I think my video card is fried. As soon as I play movies, the movie screen turns pink or green and computer freezes for a while. I know its messed up because the fan on the card came off:(. Anyways, I will be getting a new card soon. However, for the time being, I want to switch back to the on board video. I tried removing the card. But X freaked out on me, which I was expecting. I am a newb so I please help. Does comenting out the nvidia section in xorg.conf solve the problem? I do have nvidia-glx drivers installed as well. Would I need to uninstall it before removing the card?

---

### Post by renzokuken on 2007-09-03
you do not need to uninstall the drivers no.

simply change which driver your xorg uses.

you can either do this by running ```
sudo dpkg-reconfigure xserver-xorg
``` and selecting **"vesa"** as the driver

....or.....

by manually editing the device section of your xorg.conf from

```
Section Device
identifier   "blah"
**driver   "nvidia"**
End Section
```

to

```
Section Device
identifier   "blah"
**driver   "vesa"**
End Section
```

---

### Post by neon37 on 2007-09-06
Hey thanks a lot man, however, I made my old video card work again. I opened the side of my computer and put a huge window fan on my computer:lolflag: Its on max speed all the time. I also changed my video output to software rendered. So its working alrite for now not as good quality as before but works thats alrite for now. Thanks anyways

---

