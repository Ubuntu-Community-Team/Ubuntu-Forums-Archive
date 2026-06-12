---
title: "All video now runs like crap..."
date: 2008-12-21
forum: Multimedia Software
---

### Post by ownaginatious on 2008-12-21
Ever since I upgraded my tx2500 laptop to Ubuntu 8.10, the video playback has been crap. What's weird is the video is actually playing fine, but the window is flashing like mad, making the video unwatchable in the process. It didn't used to do this.

Does anyone know how to fix this? Any help would be greatly appreciated, thanks.

---

### Post by magnus0 on 2008-12-21
Try disabling compiz. Preferences -> Appearance -> Visual Effects

---

### Post by Skripka on 2008-12-21
> **ownaginatious said:**
> Ever since I upgraded my tx2500 laptop to Ubuntu 8.10, the video playback has been crap. What's weird is the video is actually playing fine, but the window is flashing like mad, making the video unwatchable in the process. It didn't used to do this.

Does anyone know how to fix this? Any help would be greatly appreciated, thanks.

Wild hunch-you don't have Amarok or a similar media player minimized to tray while this happens?

---

### Post by ownaginatious on 2008-12-21
No, I don't have anything running in the background. Everything used to be fine with 8.04. Has 8.10 broken ATI drivers or something?

---

### Post by Skripka on 2008-12-21
> **ownaginatious said:**
> No, I don't have anything running in the background. Everything used to be fine with 8.04. Has 8.10 broken ATI drivers or something?

Which apps specifically and what is your setup?

I saw some bizzarro video artifacting on Kubuntu 8.10 with VLC media player-so long as I had Amarok 1.4.10 loaded (but not playing or doing anything), hence my earlier question....When I upgraded to KDE4.2Beta2 and Amarok2, the issue has gone away in my case.

---

### Post by kiisu on 2008-12-21
I've been experiencing this but seems to be YouTube specific, any other video including other flash websites has been ok

---

### Post by utnubuuser on 2008-12-21
Try searching "upgrade broke video"

---

### Post by ownaginatious on 2008-12-21
I have the same problem for all video playing applications. The ones I've tried are MPlayer and Totem. Flash runs fine, and everything else works fine too. It's just when playing video, the window literally flickers, but the video that's playing is playing smoothly. The computer I am running this on is an HP tx2500 with the ATI video integrated.

---

### Post by cheamwei on 2008-12-21
I disabled the visual effect and it work ! no more flashing when watching movie ! yahoo :)

---

### Post by psycho on 2009-02-03
disabling compositing is the safest way to fix this problem (it can fix other problems too) but there are other options, if you want fancy compiz effects etc. and also non-flickering video.

you could try mplayer with different video drivers, for example. on my system using ati's proprietary fglrx module, video used to flicker like hell using the xv, gl or gl2 drivers, but was perfectly fine with the x11 (unaccelerated) driver. using this is as easy as:```
mplayer -vo x11 foo.avi
```or permanently via vo = x11 in .mplayer/config. with a slow processor the x11 driver might not cope with fullscreen videos however.

with the very lastest (a few days old) fglrx from ati.com these problems are fixed...almost. i was very happy to discover that compositing now works with accelerated video (and glxgears and other things that used to flicker). however, enabling xrandr rotation reintroduces the flickering problem for some reason, so now we seem to have a choice between steady video or screen rotation (or doing as you've done and disabling compositing, which enables both).

---

