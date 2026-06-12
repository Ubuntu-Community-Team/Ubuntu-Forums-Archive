---
title: "totem video codec problem"
date: 2010-06-23
forum: Multimedia Software
---

### Post by woop12 on 2010-06-23
Hi

since a few days almost (or all?) of my videos dont work in totem (totem-gstreamer) anymore. Normally this would not bother me so much because i use vlc or mplayer anyway, but as a result of this nautilus doesn't create thumbnails anymore which is very annoying.

thanks for any suggestions
woop

---

### Post by Yellow Pasque on 2010-06-23
Test out your video with:
```
gstreamer-properties
```

You can also try a more recent gstreamer repo: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

