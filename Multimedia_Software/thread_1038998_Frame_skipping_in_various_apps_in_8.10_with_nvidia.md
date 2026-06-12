---
title: "Frame skipping in various apps in 8.10 with nvidia"
date: 2009-01-14
forum: Multimedia Software
---

### Post by petsanikas on 2009-01-14
Hi all guys!

During the last days i decided to make my ubuntu 8.10 eye-candy. That is why i enabled Compiz-Fusion, AWN, Cairo-Dock, Emerald, GNomeDo (i think that's all...at least the important ones).

Unfortunately, after all these, i started having problems with video-playback. In many apps VLC, Movie Player, SMPlayer, the video playback skips some frames periodically (every few seconds ~2 or 3). It looks like it freezes for half a second. The strange thing that i accidentally noticed was that even my screensaver (the fuzzy snow flakes) behaves the same way. The flakes seem to freeze every 2-3 secs. Same thing with flash player in web-sites.

I have an AMD64 X2 and NVidia 8800GT. The video drivers i tried are 177 and 172 (i think, not at home right now).

Tried Disabling Compiz but with no luck.

EDIT: Forgot to say that by disabling the nvidia driver the problem disappears...

Could this be a kernel problem? XOrg problem? Nvidia problem? Maybe some of the new apps i installed broke something?

Please help cause right now my pc is really annoying in multimedia reproduction...

---

### Post by petsanikas on 2009-01-14
Well, guess whose fault was it... Cairo-Dock!
Closed the dock and everything is fine!

CORRECTION: Actually it was the Clock applet of Cairo-Dock when i gave it a big size (>200x200). Removing this applet fixes the problem.

I am gonna give a try to AWN and if i'm not satisfied i'm gonna dig this a bit more...
Cheers...

---

