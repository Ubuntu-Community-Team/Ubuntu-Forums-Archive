---
title: "Playing recorded .mpg in Videos instead of Recording"
date: 2009-05-04
forum: Mythbuntu
---

### Post by Sonthun on 2009-05-04
I'm going to be completely re-installing my OS and Myth, but I want to still be able to watch files I've recorded.  I would like to move them to my videos folder in the new install, but when I try to play from the videos folder I can't skip forward or back.  It just locks up the system.  I've tried the internal player, mplayer, and vlc all with no luck.  Why can the internal player play the file normally (forward skip, etc.) when in the recordings folder (and I guess listed in the database), but it can't play it normally in the videos folder.  Is there a way to fix this?

Thanks.

---

### Post by Caps18 on 2009-05-05
Have you tried Xine?  That is what I use.  

If you play the files with Xine outside of Myth can you fast forward or rewind them?  You may need to hit the space bar on your keyboard (then again it might be the right arrow, I can't remember).

---

### Post by Sonthun on 2009-05-07
Hey, that worked!  Thanks.

---

### Post by nickrout on 2009-05-07
> **Sonthun said:**
> Hey, that worked!  Thanks.

By the way why did you do this? If you'd backed up your database and restored it along with the files it would still work in the new setup.

---

### Post by Sonthun on 2009-05-07
Because the database seems to be a little bit corrupted.  Partly through computer crashes and partly because mythtv makes it really hard to change some things once they are implemented.  I made the mistake of trying to set recordings using the ota program guide that is only one day ahead.  Since I only have one day of program guide it is impossible to change a show set to record unless I'm on that day for it to show up as an upcoming recording (reported that as a bug, but got shot down).

Also, I seem to have the problem of mythtv listing a recording twice.  I'm going to fiddle with it so see if I can prevent this from happening because it is annoying.  I can't tell at glance whether I have one or two episodes of a show recorded.  I suspect this is again due to the ota program guide.  For some reason myth seems to recognize a show from the guide that I've set up to manual record and sets up two recording instances (one listing the data from the guide), but only records one file (just listed twice).  I think I'm going to completely disable the ota guide on the new install.  It's more of a pain then it is worth.

---

