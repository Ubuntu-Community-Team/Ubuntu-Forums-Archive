---
title: "Video flicker, not full screen flicker"
date: 2009-04-30
forum: Multimedia Software
---

### Post by joshh88 on 2009-04-30
The videos will play but flicker like crazy regular sized or fullscreen. The kicker is that it flickers and stops when the mouse moves. So if I continually move the mouse the flicker stops. I recently upgraded to 9.04(mistake since i recently found out my imbedded graphics isn't supported)and had to reinstall mozilla because it no longer saved bookmarks. So I'm at a loss here. I tried searching, but like the title says the entire screen doesn't flicker unless the video encompasses the entire screen. Much to my dismay all of the posts I found are complaining that the entire page and screen are flickering. That is not the case with me. That and I doubt the video card is going out yet since I had the mother board replaced recently(I'm assuming embedded video cards are embedded into the motherboard.)

---

### Post by uuilliam on 2009-07-07
Same problem
Fix needed i tried
 gconftool-2 --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows --type bool 0
and i tried gstreamer-properties fix

---

