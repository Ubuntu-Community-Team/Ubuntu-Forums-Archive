---
title: "Compiz breaks video playback"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by abds on 2007-11-23
Hi

Without compiz everything works fine, but when i enable compiz, it breaks down my video playback. When i try to play a video, the CUP usage goes up to 100%, and the video lags a lot. Ive tried everything, but cant seem to find a solution. Could someone please help me out with this. Would be extremely grateful!

---

### Post by daengbo on 2007-11-23
What version of Ubuntu are you running? What player are you using? What kind of video file is it? Does this happen with all kinds of vides, or just one (avis vd. ogg vs. mp4)?

---

### Post by shirilover on 2007-11-23
Compiz does not play well with the Xvideo overlay.
You could try enabling the Video plugin using ccsm.
I have gotten around this by patching mplayer and compiling myself; however, I still turn off compiz when I watch video sice it uses less CPU that way.

---

### Post by abds on 2007-11-24
@daengbo
Am using Gutsy, This happens with all players, and all kinds of videos. 

@shirilover
The video plugin is enabled. Still doesnt work. 
And I am playing vidoes half the time, switching compiz on and off would be too much of a hassle. Should i just turn it off then?

---

### Post by daengbo on 2007-11-24
Try this:
Hit ALT-F2
Type  "gstreamer-properties" in the dialog.
Go to the video tab.
Change the default output plugin from "Autodetect" to "X11 (no XV)"
Try to play video again.

---

### Post by abds on 2007-11-24
@daengbo

Did what you asked. The cpu usage has gone down. Though the video show up only when in full-screen mode. Otherwise its just blank.

---

