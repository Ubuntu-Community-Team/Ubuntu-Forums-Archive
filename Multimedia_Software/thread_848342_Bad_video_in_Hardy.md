---
title: "Bad video in Hardy"
date: 2008-07-03
forum: Multimedia Software
---

### Post by grenadier32 on 2008-07-03
So I upgraded to Hardy awhile ago, and ever since then my video playback has been kind of shoddy. Videos play fine, but movement is streaky--the image doesn't look good from up close, although it's a lot harder to notice from further away from the screen. It was fine before the Hardy upgrade though.

I have all the plugins that I could find installed, from Medibuntu and the regular repositories. Is there something I'm missing? Maybe something configured wrong? It happens with any video program I try except VLC, and with Totem when using both gstreamer and xine.

I'm running a laptop with a pretty old ATI RADEON x800 card, but everything seems to run more or less OK besides the video.

Any thoughts?

---

### Post by Tomatz on 2008-07-03
Open vlc go into the settings and check advanced. Then change your default output to X11.

Hopefully that will fix the issue (in vlc anyway)

---

