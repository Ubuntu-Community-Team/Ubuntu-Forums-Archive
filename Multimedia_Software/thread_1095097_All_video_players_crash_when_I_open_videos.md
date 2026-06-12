---
title: "All video players crash when I open videos"
date: 2009-03-13
forum: Multimedia Software
---

### Post by rrwo on 2009-03-13
I am no longer able to watch videos. Mplayer, Totem, Vlc, etc. all exit immediately after opening up any video file.

Was there a recent update that might have interfered with their ability to play videos?

Solution: apparently I had added the line
```
Option		"AccelMethod" "XAA"
```
to my xorg.conf file in an attempt to get Firefox to stop jambing all of the time.  Since FF still jambs up, I didn't need that. And removing it allows my video players to work.

---

### Post by rrwo on 2009-03-13
Really? What makes you think that *all* of my video playing applications are magically corrupted? Is this common? Strange, as I've never heard of it before.  Funny, too, because only the video parts were corrupted. They still play audio just fine.

Please, don't waste my time with suggestions like that. If you have no idea why, then don't post a reply.

---

### Post by cwthomas on 2009-03-15
I am also having the same problem in Ubuntu. Any video player (totem,VLC,mPlayer) will close as soon as I try to open a video file. However flash video works fine in Firefox. I've tried reinstalling codecs also but same error. Hope someone knows how to fix this.

---

### Post by rrwo on 2009-03-15
See the edited version of my original note: it might be something related to your xorg.conf, or barring that, your video driver.

---

