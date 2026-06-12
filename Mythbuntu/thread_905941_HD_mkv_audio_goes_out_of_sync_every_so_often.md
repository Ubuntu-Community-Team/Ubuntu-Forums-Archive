---
title: "HD mkv audio goes out of sync every so often"
date: 2008-08-30
forum: Mythbuntu
---

### Post by bobbob1016 on 2008-08-30
I bought an Nvidia 8400 GS pci express card with 256DDR2 onboard, 2gig on the computer, P4 3.2ghz HT.  I can watch HD without much issue, the picture quality is 1080p, no blur or anything, even when skipping forward or back.  However, when watching a movie, a 1080p movie, the audio goes out of sync every so often, and if I pause/rewind or some combo there-of, it gets back in sync.  My mplayer line is "mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:9 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 %s" from [http://www.mythtv.org/wiki/index.php](http://www.mythtv.org/wiki/index.php) which I found from this thread [http://ubuntuforums.org/showthread.php?t=808446&highlight=mkv+hd](http://ubuntuforums.org/showthread.php?t=808446&highlight=mkv+hd)  Is there an mplayer line to have it watch for out of sync audio and video?

---

### Post by Bachstelze on 2008-08-30
This is almost always a hardware problem. No solution here but upgrading.

---

### Post by bobbob1016 on 2008-08-31
There aren't many upgrades left to do, apart from the whole machine.  The video plays fine, no issues, except a pop every so often and the audio goes out of sync.  I thought there was an option to have mplayer watch for out of sync audio, but I don't know it.

Edit:  In the #ubuntu-mythtv irc channel, they said to take "-zoom -sws 0" out, since my card does that natively, and to add "-hardframedrop" so my cpu doesn't even decode frames taht won't be seen.  Seems to do the trick.  Thanks for your time.

---

