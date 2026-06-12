---
title: "Firefox Plugin for WMV 9 woes"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by matthewboh on 2007-06-28
Okay, I followed the instructions for getting the w32codecs files downloaded, but am still having troubles seeing things - for example on[ http://www.cnn.com]("http://www.cnn.com/video/player/player.html?url=/video/world/2007/06/27/chetry.townsend.humvee.attack.cnn").  If I enter ```
about:plugins
``` in Firefox, I get a long list of plugins - could there be a problem if I have wmv plugins for VLC, Totem, the Windows Media plugins?  What can I do to troubleshoot?

---

### Post by david_2001 on 2007-06-28
> **matthewboh said:**
> Okay, I followed the instructions for getting the w32codecs files downloaded, but am still having troubles seeing things - for example on[ http://www.cnn.com]("http://www.cnn.com/video/player/player.html?url=/video/world/2007/06/27/chetry.townsend.humvee.attack.cnn").  If I enter ```
about:plugins
``` in Firefox, I get a long list of plugins - could there be a problem if I have wmv plugins for VLC, Totem, the Windows Media plugins?  What can I do to troubleshoot?
I would say that you have overlapping mozilla plugins installed.  My guess is that the "Windows Media" plugin is actually mozilla-mplayer.  This works just fine - I use it myself - and happily plays the clip you linked.  The other two do not use w32codecs, at least vlc doesn't and nor does totem-gstreamer.  I've not had much success with the vlc plugin for mozilla and totem has codec support limitations, so I would recommend uninstalling those two plugins.

---

