---
title: "Pixiehollow and flash"
date: 2009-10-19
forum: Multimedia Software
---

### Post by dardack on 2009-10-19
I post a long time ago about pixiehollow and flash, now archived:

[http://ubuntuforums.org/archive/index.php/t-1015371.html](http://ubuntuforums.org/archive/index.php/t-1015371.html)

I have finally after all this time found a fix.  I found this when i recently installed 9.04 completely fresh (not an upgrade) with no copying over any user info.  For some odd reason, i was like I should see if Pixie Hollow works on a fresh install.  Installed nonfree plugin, and bam it worked.

So racking my brain, i cleared firefox's/Chromium's cache/browsing history/cache,etc.   Anything I could think of.  I was googling adobe flash cache directory linux/ubuntu, anything.  On a mac forum i found:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html)

This is a settings manage for the flash plugin, by selecting disney.com and a.dolimg.com clicking never ask again, it deletes the old data.  This then allowed me to log back into pixiehollow again.  This was confirmed on 2 separate ubuntu 9.04 and 8.10 where it did not work before.

I know I had a few people post they had same issue, so posted how I fixed it.  FYI you can't just delete the websites from the list, i tried that first, but it  doesn't seem to really delete the data unless you select never ask again when disney/a.dolimg are selected.

Also, want to thank Adobe for a flash settings manage i never knew about.  Am I the only one?  Have i really been in the dark about that this long?  Sigh.  Hope this helps someone else.

EDIT: Setting it  back to store data caused the same thing. So now i  just leave it as never store data.  Doesn't seem to affect game play.

---

