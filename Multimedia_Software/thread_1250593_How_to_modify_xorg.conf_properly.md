---
title: "How to modify xorg.conf properly?"
date: 2009-08-26
forum: Multimedia Software
---

### Post by ZCP M3 on 2009-08-26
Hey all,
I'm using 9.04 as a base to run XBMC off of an NVIDIA ION platform and it seems that some editing of the xorg.conf file needs to be done to access the proper resolutions for proper video playback.

That being said, anytime I edit xorg.conf, Ubuntu freaks out and sends me into low-graphics mode.

What is the proper way for me to edit this config file?

Edit: I'm running NVIDIA's latest 185.18.36 drivers on a *fresh* install of 9.04 that has been updated. Nothing loaded on it.

---

### Post by inobe on 2009-08-26
it's always best changing the res threw nvidia settings.

```
gksu nvidia-settings
```

---

