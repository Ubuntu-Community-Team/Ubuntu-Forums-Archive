---
title: "HD playback issues"
date: 2011-05-30
forum: Multimedia Software
---

### Post by brinker on 2011-05-30
Well, I've just built a new HTPC, with the ASRock E350M1/USB3 and 2GB Kingston DDR3 1066MHz. I'm running Ubuntu 11.04, and I've followed the ATI driver guide, seeing that there has been some issues with this earlier.

I'm using XBMC for video playback, this has given  the best results so far. 720p runs smooth, but 1080p is no near smooth.
It's from .mkv files - is there any player that might do better? I have tried VLC, can't even playback 720p smooth. Hardware acceleration is enabled.

---

### Post by BicyclerBoy on 2011-05-31
You do realise this is a Zacate/fusion CPU/GPU beast ?

The video decode acceleration comes from using VA-API.
Have you set up VA-API ? & build XBMC with VA-API support ?

My guess is you are getting CPU decode only..

Search for:
zacate fusion e350 apu splitted-desktop va-api
The best guide to getting Fusion to work that I have found is on XBMC forums..

To test from terminal run..
vainfo

There are some doubts if this AMD APU is able to do VA de-interlacing, this is required to make ideal HTPC box.

---

### Post by brinker on 2011-05-31
Nope, I'm pretty new to Ubuntu, so I haven't done that much yet. I'll look into it when I get home today :)

---

### Post by BicyclerBoy on 2011-05-31
Here's the link,

[http://forum.xbmc.org/showthread.php?t=81286](http://forum.xbmc.org/showthread.php?t=81286)

I think you need a specific version of AMD catalyst driver & VA-API from splitted-desktop.
This is not a simple PnP job ..but not impossible.
I can't help you any further..
Good luck.

---

