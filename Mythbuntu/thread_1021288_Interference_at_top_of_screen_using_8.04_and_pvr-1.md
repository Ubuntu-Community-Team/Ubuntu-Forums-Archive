---
title: "Interference at top of screen using 8.04 and pvr-150"
date: 2008-12-25
forum: Mythbuntu
---

### Post by gcole on 2008-12-25
I have a myth system using a backend with 2 pvr-150's in it, running 8.04.  Hardware is an Intel 865 glc motherboard, using the onboard graphics and a p.4 2.4b.

Anyway, everything works great but for some reason, every recording I have gets a line of interference across the top of the screen.  I have a couple of front ends that all use different graphics cards for playback (nvidia and ati) and it is present in all of them, so it is something with the PVR-150 recording.  I have 2 pvr-150's and they both have it.  It is only about 4 pixels wide, otherwise the picture is clear.  I've attached a screen capture from mythplayer under windows

[http://picasaweb.google.com/lh/photo/bWCTpSzTZvyklLRQoOxtsg?feat=directlink](http://picasaweb.google.com/lh/photo/bWCTpSzTZvyklLRQoOxtsg?feat=directlink)

Seems like I need to adjust the offset for the recordings somehow, but I'm not sure how to do that.  I've tried to cover it up by shifting the image using the front end playback settings, but I would like to try to fix it at the recording stage instead.

Any suggestions?

Thanks,
Greg

---

### Post by zoiks on 2008-12-25
I'm not 100% sure but it just looks like VBI data to me. That data is always there - you just have to adjust overscan or screen dimensions to get rid of it.

---

### Post by gcole on 2008-12-25
where in myth do you adjust these settings?  I've tried changing the screen position with the front end, is there some way to adjust it from the backend so that it is not visible on the recordings?

Greg

---

### Post by zoiks on 2008-12-30
I don't know of a way to "remove" it from the recordings. It occurs in a portion of the video that's not meant to be displayed (the vertical blanking interval, which includes the first few scan lines). You get rid of it in the playback mode, by adjusting your screen or overscan settings in the player (i.e. in the frontend setup).

---

### Post by ian dobson on 2008-12-30
Hi,

Check your recording profile/tuner profile and make sure your using the correct signaling (Here in switzerland we have PAL-BG) see [http://icecube.berkeley.edu/~dima/stuff/comp/vstandards.html](http://icecube.berkeley.edu/~dima/stuff/comp/vstandards.html)

Regards
Ian Dobson

---

