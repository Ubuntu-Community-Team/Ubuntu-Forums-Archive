---
title: "Herky Jerky matroska vids in mplayer"
date: 2010-07-26
forum: Multimedia Software
---

### Post by selittl on 2010-07-26
I can run matroska vids fine in VLC, but would like to use mplayer.  vids are too jerky to play.  running latest nvidia drivers and such.  any ideas?

---

### Post by cchhrriiss121212 on 2010-07-26
Try selecting a different video output, if you have a decent card then you should be able to use vdpau hardware acceleration output.

---

### Post by selittl on 2010-07-26
I have an Invidia ion card with 195.xx drivers installed.  I see no options to use vdpau output on the invidia x server settings.  Might this option be elsewhere?

---

### Post by cchhrriiss121212 on 2010-07-26
The option will be on the video player itself. If you use smplayer as a frontend, then just go to preferences and select vdpau under video output.

---

### Post by RiceMonster on 2010-07-26
> **selittl said:**
> I have an Invidia ion card with 195.xx drivers installed.  I see no options to use vdpau output on the invidia x server settings.  Might this option be elsewhere?

edit ~/.mplayer/config and add this line:

vo=vdpau

---

### Post by rubylaser on 2010-07-26
I don't believe that the mplayer in the repositories supports VDPAU.  I use XBMC to play all my videos, and VDPAU works out of the box.  But you could try to follow these instructions...
[http://ubuntuforums.org/showthread.php?t=1037625]("http://ubuntuforums.org/showthread.php?t=1037625")

EDIT: Yes the version in 10.04 does.  So disregard what I said.

---

### Post by selittl on 2010-07-26
I changed the mplayer output to vdpau and it works much better now!:D

Thanks

---

### Post by selittl on 2010-07-27
I enabled vdpau in mplayer and it now works much better.  Still an issue with a couple files, but I will chalk that up to bad file container issues.

Thanks!

And yes...xbmc works just fine out of the box as does VLC.  Don't know why I feel I need mplayer to work also :)

---

