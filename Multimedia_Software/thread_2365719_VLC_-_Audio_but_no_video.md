---
title: "VLC - Audio but no video"
date: 2017-07-09
forum: Multimedia Software
---

### Post by oygle on 2017-07-09
If I try any MP4 file, I get audio but no video, using VLC. Yet if I try MPV media player or even Firefox, the MP4 has audio and video.

Hard to estimate exactly, but about 4 days ago, VLC was fine, so I was thinking of an update ?? Have made sure all updates are done, plus completely uninstalled VLC and installed it again. Still no video.

Here are the messages from VLC

> 
vdpau_display error: output surface creation failure: A catch-all error, used when no other error code applies.


about 500 of these messages, after only playing for a few seconds.

VLC version is 2.2.2 Weatherwax

---

### Post by vasa1 on 2017-07-10
See if [https://forum.manjaro.org/t/only-sound-in-vlc-player/26631/5](https://forum.manjaro.org/t/only-sound-in-vlc-player/26631/5) helps.

---

### Post by mc4man on 2017-07-10
For starters open vlc > Tools > Preferences and set under Input/Codecs the 1st option to Disabled & in the Video tab pick OpenGl.. as in screens, Click save & try vlc again.

---

### Post by oygle on 2017-07-10
> **mc4man said:**
> For starters open vlc > Tools > Preferences and set under Input/Codecs the 1st option to Disabled & in the Video tab pick OpenGl.. as in screens, Click save & try vlc again.

Thanks 'mc4man'. I did the first one as per your post, still no video, and then when I set the Video tab, it worked, now have audio and video.  :D

> **vasa1 said:**
> See if [https://forum.manjaro.org/t/only-sound-in-vlc-player/26631/5](https://forum.manjaro.org/t/only-sound-in-vlc-player/26631/5) helps.

Thanks 'vasa1'; I read the post and will keep it in mind for future. i did wonder about emptying the .config/vlc folder as it may have needed to reset to defaults. If possible, need to keep away from nvidia drivers, as the computer is nearly 9 yrs old, so the video card only runs well with Nouveau (free driver).

---

### Post by kana-kanji2000 on 2018-01-22
this post was the one that worked for me, I finally have video. Who would say that the new version enables hardware acceleration.

---

