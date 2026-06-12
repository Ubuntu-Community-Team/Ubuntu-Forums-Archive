---
title: "Playing DVD movie not stable in Totem Player"
date: 2009-04-13
forum: Multimedia Software
---

### Post by hosoka on 2009-04-13
All,

I am using the Totem player with my Ubuntu 9.04 and wanted to play a DVD on it. Found out that the movie is not playing correctly as it kept on rolling up and down, just like previous days when you need to tune the TV to have the screen stable :-).
I've checked out also with VLC player, but still the same.
Downloaded all the Gstreamer plugins but no good.

Did I've missed something to install or to check ?

---

### Post by UbuntuNerd on 2009-04-13
are you sure you installed all the right plugins and codecs?

---

### Post by hosoka on 2009-04-13
As far I can remember is that when I search in Ad/remove programms I highlighted all the gstreamer codecs. 

Will let you know later to see if I've missed something. What I don't get is that also in VLC player the video is not playing stable. That's a bit weird. 

To be more precisely is that when you watch the movie or any other DVD I see, there is a line that comes from the top and then down and over and over again. Very annoying actually.

---

### Post by hosoka on 2009-04-14
Issue solved.
I've dowloaded all Gstreamer plugins and install the video driver of Nvidia. Think it is because of the DVD codecs that were missing to playback encrypted DVD.
Case closed.

---

