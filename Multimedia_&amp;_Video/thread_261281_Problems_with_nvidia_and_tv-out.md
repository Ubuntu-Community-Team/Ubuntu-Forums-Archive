---
title: "Problems with nvidia and tv-out"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by phear_me on 2006-09-20
I have got some problems with my nvidia and tv-out.

LCD works, but TV doesn't.



My xorg.conf - [www.lietus.org/downloads/xorg.conf]("www.lietus.org/downloads/xorg.conf")
Xorg logs - [www.lietus.org/downloads/Xorg.0.log ]("www.lietus.org/downloads/Xorg.0.log")

Maybe because of this :
```

(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.


```

Any ideas?

---

### Post by agkbill on 2007-12-25
Hi,

I'm having the same problem. It looks like it have to do with the type a cable you are using from the videocard to the TV. S-video or composite. composite makes the card detekt the TV no picture, S-video OK picture but I cant get the card to detekt.

---

### Post by adelodder on 2007-12-25
Have you tried to install the latest drivers with envy?  [link]("http://albertomilone.com/nvidia_scripts1.html")

It worked like a charm for me although I don't use a svideo cable.

---

