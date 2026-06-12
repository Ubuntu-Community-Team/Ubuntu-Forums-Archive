---
title: "Why won't mplayer autolad subtitles?"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by KeeperOS on 2008-02-03
Well, that. After a hell of a lot of searching I found those 3 little commands that will allow mplayer to properly load SSA/A-SS styled subtitles with embedded fonts.

However how I can tell it to auto-load those subtitles still eludes me.
It's a little annoying to have to get up and manually choose a subtitle stream, it can't be that mplayer can't be set up to automatically load the first (default) stream by itself, can it?

---

### Post by gsmanners on 2008-02-03
mplayer -sid 0

(0 = first track, 1 = second track, etc.)

---

### Post by KeeperOS on 2008-02-03
Thanks!!!

Will it work in the config file as well?
(i.e.
```
ass=1
embeddedfonts=1
correct-pts=1
sid=0 (or 1)
```

Sth like this?

---

### Post by smartalek65 on 2008-07-16
A quick test shows that adding the line "sid=0" to the mplayer configuration file does work.

For those who don't know, the mplayer configuration can be found by pressing ctrl + H in the home folder, navigating to ".mplayer". It is "config".

---

