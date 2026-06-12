---
title: "Firefox Xine-Plugin doesn't work"
date: 2008-09-05
forum: Multimedia Software
---

### Post by darundal on 2008-09-05
Hi, does anyone know how to get the firefox xine-plugin working? I installed the package from the repos. Whenever I try to view an embedded non-flash video or audio file, Firefox goes tits up. Anyone have any ideas how to fix this (not switching, but actually fixing the issue)?

---

### Post by gandaran on 2008-09-05
did you remove the totem plugin? did the totem plugin work or not?

xine-plugin is very good for online streaming and so is the totem-plugin, but if you have problems with totem then you'll probably have with xine too.
did you install the gstreamer codecs for totem?
can you post the link you trying to play/view?

---

### Post by darundal on 2008-09-05
Yes I removed the totem plugin, which worked fine. I just prefer not to have extra cruft on my system, and I prefer Xine as a video player to Totem or VLC or Mplayer. Yes I installed the gstreamer codecs, and I was trying to watch the video on [this]("http://www.ketv.com/news/17396704/detail.html?rss=oma&psp=news") page. I also tried to listen to a wave file from [here]("http://radost.org/New/index.php?nav=iap.php&id=126") to test to see if it was just that one page.

With the totem plugin, it showed the little can-not play icon thing. With the xine-plugin it just crashes. The WAV file I know works with totem. I try to listen in the browser with the xine-plugin and it crashed Firefox.

---

### Post by gandaran on 2008-09-06
> **darundal said:**
> Yes I removed the totem plugin, which worked fine. I just prefer not to have extra cruft on my system, and I prefer Xine as a video player to Totem or VLC or Mplayer. Yes I installed the gstreamer codecs, and I was trying to watch the video on [this]("http://www.ketv.com/news/17396704/detail.html?rss=oma&psp=news") page. I also tried to listen to a wave file from [here]("http://radost.org/New/index.php?nav=iap.php&id=126") to test to see if it was just that one page.

With the totem plugin, it showed the little can-not play icon thing. With the xine-plugin it just crashes. The WAV file I know works with totem. I try to listen in the browser with the xine-plugin and it crashed Firefox.

then I'm surprised, I always believed xine plugin was the best, I used it some time ago, it never failed where others didn't work.  
tried your link, the small video works very well in firefox/toten-plugin, for the opera browser, I use the mplayer-plugin, didn't work, which is no surprise, mplayer fails a lot of times.
check if **libxine1-ffmpeg** is installed, install the w32codecs too, xine can use some of them.   
sorry I can't be of any further help.

---

### Post by piotrp1504 on 2009-01-19
> **gandaran said:**
> then I'm surprised, I always believed xine plugin was the best, I used it some time ago, it never failed where others didn't work.  
tried your link, the small video works very well in firefox/toten-plugin, for the opera browser, I use the mplayer-plugin, didn't work, which is no surprise, mplayer fails a lot of times.
check if **libxine1-ffmpeg** is installed, install the w32codecs too, xine can use some of them.   
sorry I can't be of any further help.
Thanks a lot libxine1-ffmpeg is the only problem for me, I mean was ;)

---

