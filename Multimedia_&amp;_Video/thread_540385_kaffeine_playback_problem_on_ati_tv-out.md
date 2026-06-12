---
title: "kaffeine playback problem on ati tv-out"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by bogdan2412 on 2007-09-01
I have kubuntu feisty fawn with ati drivers 8.40.4 installed manually. I've hooked my laptop to my TV to test TV Out and after some time I got the standard that works with my TV (using the catalyst control center, atitvout didn't really work, it kept reverting to the original standard and didn't really do anything) Only problem is when trying to play a video in kaffeine. I only get a black window. glxgears and fgl_glxgears works fine on the other hand. Don't know what to do. Video playback was the main reason I actually wanted to try the tv out :(

---

### Post by Placenta Juan on 2007-09-08
Same problem here. I have a Radeon 9600XT with the 8.40.4 drivers. I noticed in the release notes for the 8.40.4 driver that "There is no support for video playback on the second head in dual head mode."  I'm wondering if the s-video out can be made the primary head, and the monitor the secondary? It would be a pain, but I have no dvd player and it would be nice to be able to watch dvds on my tv through my computer's dvd-rom drive. TV out seems kind of pointless if it won't play video...

---

### Post by Placenta Juan on 2007-09-09
OK, if you go settings>xine Engine Parameters in Kaffeine, click on video on the left, and then change the video driver to opengl, video should play back on the tv out. The only problem now is that I can't figure out how to change the resolution on the tv screen independent of the primary monitor, making full screen playback larger than the actual tv display, unless I turn the resolution for my monitor down to 640x480.

---

