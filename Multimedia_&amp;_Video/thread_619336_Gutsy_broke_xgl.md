---
title: "Gutsy: broke xgl"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by jorphis on 2007-11-21
I had XGL + compiz working before on my AT Ix300 mobile card.  I tried to change some stuff (it wouldn't expand to its native resolution) and it broke everything.  I fixed it all by removing a lot of stuff and putting it back 1 by 1.  I found the problem to be xgl.  I couldn't login while xgl was enabled, I would have to go to safemode and remove it.  Thinking there was some residual config file that was causing the problem, I searched the file system for xgl thinking I would delete said leftover file.  The only file I found that I thought could possibly be the problem was in /etc/X11/Xsession.d/  (I forgot the name of the file, it was long and had numbers in it).  Anyway I deleted it and everything booted fine, but without xgl.  So I figure this is the file that launches xgl as part of gnome now.

So In summary: I was wondering if anyone could tell me how their file is named and what the contents are and what purpose it serves?

Also, besides uninstalling with the package, is there a way to completely remove xgl, so I can install it from scratch?  (when I was reinstalling it, it never gave the message about how xgl is now combined into gnome like it did the first time, so I concluded it wasn't fully uninstalling it)

---

