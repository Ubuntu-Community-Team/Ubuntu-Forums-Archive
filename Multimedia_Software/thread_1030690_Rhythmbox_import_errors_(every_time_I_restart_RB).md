---
title: "Rhythmbox import errors (every time I restart RB)"
date: 2009-01-04
forum: Multimedia Software
---

### Post by mpc350 on 2009-01-04
So, I have all the gstreamer plugins, etc, and have a dual boot system.  I have all media on iTunes in the windows partition and just link to it with Rhythmbox.  Of 8k+ files, I get ~440 import errors.  That is fine, those are DRM'ed music and I dont expect to be able to use them with RB.  The problem is that for 5 minutes after I start RB, it tries to re-import all of those files and re-finds the ones that wont work and creates a new import errors list, also using up a hefty bit of CPU power.  

Is there a way to tell RB to remove these non-working files from its' playlist so we don't have to go through this every time I relaunch it?  I COULD go through all music in the RB library and manually delete the ones that don't work, the problem being, once they've been found out to not work, it takes them from the library list and sticks them in the import errors list.  

Thanks in advance.

Matt

---

### Post by rossmoore on 2009-04-20
I'm finding this behaviour too, and I'm not sure what's causing it:
1. I have just upgraded to Jaunty RC, with a fresh install.
2. I have also changed my home folder setup: I now have a symblic ilnk pointing from /home/Music to another (ext3) partition on the same drive.

To re-iterate: every time I start Rhythmbox it scans my music folder, finds files that it can't import (that it has already encountered before) and tries to import them again - reporting plugin errors which I have to click away 7 times (once for each plugin type). I would expect Rhythmbox to only try to import a file once automatically.

---

### Post by rossmoore on 2009-04-20
There is an as yet (Januty RC) unfixed bug related to this:

[https://bugs.launchpad.net/rhythmbox/+bug/204566](https://bugs.launchpad.net/rhythmbox/+bug/204566)

---

