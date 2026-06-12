---
title: "Problems with video (avi, mpeg etc. not working)"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by Kihu on 2007-10-03
Hey. I recently installed Ubuntu 7.04 and this is the first time for me using Linux. So far everything looks good, but when it comes to playing movies there are problems. In short, when trying to play something, lika a .avi movie, I can hear the sound, but the picture doesn't show up. I have tried with Movie Player and VLC Media Player.

I have the following codecs installed:
GStreamer extra plugins
GStreamer ffmpeg video plugin
Gstreamer plugins for aac, xvid, mpeg2, faad
GStreamer plugins for mms, wavpack, quicktime, musepack
Ubuntu restricted extras
libdvdcss2 
w32codecs

Most of the other threads suggested installing some of those, but to me they have been of no help. Any suggestions as to what could I try next will be most appreciated.

My setup:
Acer 5021 WLMi
ATI Mobility Radeon X700
Samsung Syncmaster 205BW 20" widescreen (as the main display, my laptop's screen is blank)
I'm using the default ATI drivers

---

### Post by hardyn on 2007-10-03
Exactly the same problem... however i could play these files a few days ago?

hmm... seems to be fixed now... but im not sure what i did?

---

### Post by RomeReactor on 2007-10-03
Hi. That may have to do with having an ATI card and desktop effects enabled; try disabling the effects, or [this workaround from UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback").

---

### Post by Kihu on 2007-10-03
Thanks for the info! That works for me :). I actually found out the same thing just a few minutes ago while randomly browsing this site. [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357) <- This is where I found the same instructions. Apparently the issue didn't have anything to do with desktop effects, though (i had them disabled).

---

