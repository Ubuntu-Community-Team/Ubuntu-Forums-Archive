---
title: "No video in players, but sound."
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by Ajiah on 2007-06-10
Hey everyone! Linux noob here! (I just wanted to get that out of the way to avoid any possible terminology that I have yet to learn. :D)

   I am loving Ubuntu so far, but I have yet to get video to work properly. I have tried VLC, MPlayer, and even the pre-installed video player. Generally speaking, I can get sound up, but no video. If I move or resize the video, I might catch a short glimpse of a frame, but it turns to black right afterwards.

  Help would be appreciated! (Oh, and the video is AVI format, if that says anything. I can't play other formats either.)

---

### Post by Error1312 on 2007-06-10
Not sure, but maybe you don't have the right codecs installed?

Try this command to install them:

sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs

Or check this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs")

---

### Post by Ajiah on 2007-06-10
Eh, it took a while, but I found out that the problem is Beryl. For some reason, the effects Beryl implements messes with video on some machines. I had to change VLC and Totem output to a different output source. 

 Problem solved! (Next time I will search a bit more before posting. Thanks for the help, anyways!)

---

### Post by drakeskywing on 2007-06-11
Hey Ajiah, i poked around VLC, and i don't really understand how you mean by changing output sources, could you be a little more detailed into how to fix it, cause i am suffering the same result due to beryl

---

### Post by Ajiah on 2007-06-11
Oh, yeah! Sorry about that, bud.

 You go to Settings >> Video (Click Advanced options at the bottom) and select "X11 Video output". 

 Hope it works! Let me know either way.

---

### Post by drakeskywing on 2007-06-25
Cool thanks for that, now i just got to reinstall beryl, but thanks for the help

---

### Post by happyxix on 2007-07-04
... I can't find this X11 thing in vlc.. where is it exactly? I got up to the part with the clicking advance options..

---

