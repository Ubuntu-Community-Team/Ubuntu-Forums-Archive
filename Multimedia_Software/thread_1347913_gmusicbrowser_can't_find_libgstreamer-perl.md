---
title: "gmusicbrowser can't find libgstreamer-perl"
date: 2009-12-06
forum: Multimedia Software
---

### Post by strungoutfan78 on 2009-12-06
I recently switched music players to gmusicbrowser.  Everything worked fine on it, including the album cover art.  All of a sudden, no album cover art.
When I run it in a terminal it gives me this nonsense:
```
GStreamer::Interfaces perl module not found -> visuals not available

```

Now if I run gmusicbrowser as root it loads all modules and cover art just fine.  I've tried purging both gmusicbrowser and libgstreamer-perl and reinstalling, but no luck.  Even tried downloading the latest version of gmusicbrowser from the website.  Nothing.  Why could this happen?  I've changed all permissions of my music library to 0755 just in case and that had no effect either.

I should mention this is on an amd64.

---

### Post by Yellow Pasque on 2009-12-06
Installed libgstreamer-interfaces-perl package?

---

### Post by strungoutfan78 on 2009-12-07
Ha actually no I didn't have to do any of that.  I knew better than to post this question.  Just like all the rest I figured it out within 15 minutes of my original posting.  Something screwy with the way gmuscibrowser saves tag backups in ~/.config/gmusicbrowser.  I simply deleting the quadruple copies of backups and everything else other than the layout and icon folders.  Bingo.  Kinda weird.  Thanks for the reply. :guitar:

**edit**Oh and just for the record it still can't find libgstreamer-perl!

---

