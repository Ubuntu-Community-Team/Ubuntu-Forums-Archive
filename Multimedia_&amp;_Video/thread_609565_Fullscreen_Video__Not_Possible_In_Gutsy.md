---
title: "Fullscreen Video  Not Possible In Gutsy"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by derubermensch on 2007-11-11
In both Totem and Mplayer, I cannot achieve full screen video.  In Mplayer it simply keeps the same size video and envelops it in black, while in Totem the video is resized to fit the height but not the width, such that black bars are parallel to the height on left and right.  I've used the fullscreen/zoom console command on mplayer to no avail.  Suggestions?

---

### Post by jerinjoy on 2007-11-11
I had an issue with fullscreen with compiz/beryl enabled. try disabling the eye candy and see if it works.

System->Preferences->Appearance->Visual Effects

Set to None and then try playing a Video.

---

### Post by derubermensch on 2007-11-11
That was actually the first thing I did.

---

### Post by pendrachken on 2007-11-11
try using a different video output in mplayer, such as Xv or oepngl or opengl2. 

you are most likely using Xshm right now, and video resizing is not really supported.

---

