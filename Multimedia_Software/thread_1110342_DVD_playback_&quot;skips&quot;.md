---
title: "DVD playback &quot;skips&quot;"
date: 2009-03-29
forum: Multimedia Software
---

### Post by velozoom on 2009-03-29
Ubuntu intrepid, fully updated on a thinkpad T500 w 4Gb RAM.  Using the ATI FGLRX driver.  For the most part, the system works flawlessly.  Compiz, flash video, etc.  All working very nicely.  

Popped a DVD in for the first time last night and noticed that approximately every 5 seconds there is a momentary glitch in the video playback.  It's a very brief hesitation.  It only lasts for a fraction of a second, just enough to be noticeable actually, and there is a corresponding hitch in the sound.  

I'm using VLC which I've never had an issue with before.  The same glitch occurs in mplayer and gxine.  

Not really sure where I should start looking since everything else seems to be working fine.  Haven't had any issues with the DVD drive, it reads other types of discs with no discernible hesitation although I can't really tell since they aren't doing playback.  A search didn't turn any results I felt were applicable.  

Any thoughts?

---

### Post by Taus on 2009-03-29
not sure if it will work, but i had a similar problem in gentoo a while ago. i used "hdparm -d1 /dev/cdrom0" change the /dev/cdrom0 to your dvd device.

hope it works :)

cheers

---

