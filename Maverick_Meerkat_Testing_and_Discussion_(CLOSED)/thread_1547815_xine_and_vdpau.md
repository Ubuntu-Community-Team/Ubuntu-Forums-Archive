---
title: "xine and vdpau"
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tcchris on 2010-08-07
Hi ,
I just installed Meerkat , no probs so far , except I have no vdpau option in xine . I had this problem with Lucid also .
I have vdpau installed but it is not an option in xine .
This is important to me because Me-tv uses xine and OTA 1080i tv is difficult to watch without vdpau .

---

### Post by mc4man on 2010-08-07
I don't see any indication that a vdpau enabled xine will be in 10.10.
(the same for a vaapi vlc, nor gstreamer (vaapi ?

Why the reluctance not too sure.
Anyway, did a build of the latest xine-lib-2-1 and xine-ui - it works ok, but not that impressive. This could be the state of dev and or my particular hardware. (I find the same deal with vlc 1.1.2 w/ vaapi

On the other hand mplayer w/ vdpau  ranges from incredible w/ h264 to ok with vc1 and wmv3

If you're not inclined to build then look for a ppa  - more likely near or after the maverick release
This one is a good candidate, ck. every once and a while to see if the added maverick (maverick should be quite easy for them to add

[https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia](https://launchpad.net/~nvidia-vdpau/+archive/cutting-edge-multimedia)

Edit: you may be able to use the lucid xine-lib and xine-ui packages from there on maverick - no need to try here, no big deal to try..

---

### Post by tcchris on 2010-08-07
Thanks , I thought it would be included in maverick , I will try the ppa .

---

