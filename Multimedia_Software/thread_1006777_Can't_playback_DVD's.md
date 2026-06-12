---
title: "Can't playback DVD's"
date: 2008-12-09
forum: Multimedia Software
---

### Post by residualbit on 2008-12-09
So I bought the new batman movie today, and I wanted to watch it on my laptop which runs hardy but i can't. I followed the instructions here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

and even set the region code to 1, but to no avail. Help!

I am trying to use totem movie player. I also tried vlc, but it just plays really broken up audio and no video.

---

### Post by residualbit on 2008-12-09
sorry.bump.

---

### Post by mc4man on 2008-12-09
Try changing your audio and video outputs which are generally set to default. The idea ia to pick something and see.

_Assuming your using vlc 0.8.6_

Go settings -> preferences and click "show advanced options".
Then expand the Video tree and highlight 'Output modules', on the r. side will be your drop down.

The preferred is "XVideo ..." you can try that though it may not help. If not try "X11 .." and then finally "OpenGl".

Also do the same for audio output module, in this case the best bet is to choose 'alsa..'

Don't forget to click save between setting changes.

Gstreamer apps and system wide is usually adjusted in System -> Preferences  both in  "Sound" and "Multimedia Systems Selector"

If you can get your audio and video going in vlc but have navigation issues then right click on Applications -> edit menus. Scroll down to Sound & Video and highlight it. In the right side panel, right click on Vlc -> properties.

Change the command to vlc %f (just replace the U with an f


Edit: the easist way to set vlc as default in hardy

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

For all other players and various methods ect.

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

