---
title: "mythtv changing the default player to totem"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by bone2006 on 2007-08-28
mplayer's audio seems to be off, so I wanted to go with totem and I played around with settings and put in "totem --fullscreen %s" and it seems to run full screen, but when I fastford I don't see the status bar I saw with mplayer.  Is that just an mplayer settings or should I put something else in mythtv's default player settings?

mplayer -framedrop -monitoraspect 16:9 -fs -zoom -quiet -vo xv -alang en -ao oss %s

I saw this posted somewhere else for VLC
vlc file://%s vlc:quit

I like VLC, but the full screen isn't working, so would like to get totem going.  The video and audio seem to run perfect

---

