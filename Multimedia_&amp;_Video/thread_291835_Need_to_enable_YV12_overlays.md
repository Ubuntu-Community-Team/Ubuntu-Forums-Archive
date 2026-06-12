---
title: "Need to enable YV12 overlays"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by roadkill on 2006-11-03
I'm using an Aspire 5001WLMi with an SIS video card running 661/741/760/761 PCI/AGP VGA Display drivers.  I'm also running xine with xine-ui as an interface.  When I attempt to play a DVD that way, xine throws up an error message complaining of 'too many dropped frames'.

When I run xine-check, it tells me that YV12 overlays are not enabled, forcing xine to do colour space transformation and scaling in software.  I haven't found anything related to YV12 overlays in documentation, or on the forums or wiki.  Can anyone tell me now to enable these?

---

### Post by Qushu on 2006-11-04
Hi 
I have the same problem. I have an Aspire 5672 and my graphics card is X1400. Addition to that problem I can't watch DVDs either none of the players (gxine, xine, mplayer, vlc, totem) work with my DVDs. I have a feeling that if I can activate this YV12 layer stuff all my problems will be solved :) Any kind of ideas are welcomed.

---

### Post by whatever on 2006-11-04
as far as i know it is impossible to get YV12 with X1k-series cards at the moment. the old radeons based on r300/r400 still got a 2d core which can do real YV12 overlay. with the X1k series this core got removed and for these cards the pixelshaders are used to emulate overlay, and apparently ati did not implement YV12 (yet?).

as mplayer can do very fast colorspace conversion, i'd suggest that you use mplayer with opengl output for watching dvds. try this command:
```
mplayer -vo gl:yuv=2 dvd://
```

edit: the yuv=2 thing will make mplayer use your graphics card's pixelshaders for the conversion. yuv=0 would result in pure software colorspace conversion, but the scaling could still be done in hardware.

---

