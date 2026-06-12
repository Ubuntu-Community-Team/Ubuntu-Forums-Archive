---
title: "Very Poor Refresh Rate"
date: 2011-06-05
forum: Multimedia Software
---

### Post by jamgood96 on 2011-06-05
I just built a home media server. It's using a Gigabyte E350N-USB3 motherboard with the AMD Fusion processor. So far, everything seems to be working fair enough. However, when it comes to video playback via an HDMI cable to my TV, it's unwatchable. It is okay during slow scenes, but any sudden movement or high action scenes and the problem becomes obvious.

I don't know how to explain it other than it appears to have a problem refreshing quickly enough. I see horizontal lines across the film. I originally thought it might be due to low quality AVI files, but I just tried a DVD and it did it just the same.

I'm pretty knew to Ubuntu, so I'm not sure if there are some settings I can tweak, or if I am missing some drivers. Any ideas on where to start?

---

### Post by wolfen69 on 2011-06-05
What kind of video card do you have? You may need to install the drivers for it.

---

### Post by jamgood96 on 2011-06-05
> **wolfen69 said:**
> What kind of video card do you have? You may need to install the drivers for it.

AMD Radeon HD 6310

---

### Post by BicyclerBoy on 2011-06-05
The AMD fusion/zacate is an APU  CPU/GPU combo.
The best feature is really the price.

The best HTPC zacate set-up is, possibly, on XBMC forum..

[http://forum.xbmc.org/showthread.php?t=81286](http://forum.xbmc.org/showthread.php?t=81286)

You need a specific AMD catalyst driver possibly modified.
VA-API library from splitted-desktop systems.

You then need VA-API support in your media player.
Most require custom build or 3rd party ppa to get VA-API..

XBMC & VLC have to be re-compiled for VA-API.
mplayer may work out of the box but this is not really a media centre app.

---

