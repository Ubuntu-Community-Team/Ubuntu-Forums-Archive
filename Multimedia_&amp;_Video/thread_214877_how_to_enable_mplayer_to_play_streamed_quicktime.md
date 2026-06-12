---
title: "how to enable mplayer to play streamed quicktime"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by kris2pe on 2006-07-13
I have already tried setting up totem-xine & then installed firefox-totem -gstream-plugin to enable mplayer. But to no avail the xine player pops up & crashes while playing the video.

---

### Post by timetunnel on 2006-07-13
There's a package "mozilla-mplayer" in the "multiverse" repositories. I simply installed that and it worked fine out of the box.

---

### Post by bsalt on 2006-08-17
> **kris2pe said:**
> I have already tried setting up totem-xine & then installed firefox-totem -gstream-plugin to enable mplayer. But to no avail the xine player pops up & crashes while playing the video.

i have the same problem. i want to view their keynote speach on [www.apple.com](www.apple.com), but i can't.

---

### Post by kerry_s on 2006-08-17
Totem clashes with mplayer. you can remove the shortcuts in /usr/lib/firefox/plugins so only mplayer is used or just uninstall the totem plugins, after that mplayer should work with out problems. you need mplayer,mozilla-mplayer, and w32codecs to play just about all videos.

---

