---
title: "can't delete feed in rhythmbox"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2007-06-19
I deleted some podcast episodes in rhythmbox and now I want them back, but it refuses to download them now.  So now I want to just remove the feed (or even all the feeds) and just start over.   But I can't get rhythmbox to "forget about" the feed.  Even removing rhythmbox with "apt-get remove --purge" didn't work!  When I reinstalled, it still "remembered"!  ARGGGG.

---

### Post by Sonofmoog on 2007-06-19
Try deleting the files in ~/.gnome2/rhythmbox.  Riskier.. maybe a lot riskier .. is to try deleting one or more of the files here:

$HOME/.gconf/apps/rhythmbox/

such as, .. /state/podcast/%gconf.xml

---

### Post by Lary Grant on 2007-06-19
Brilliant!!!  I had looked for those pesky dot directories before, but I didn't think of looking under .gnome2.  So I went into rhythmdb.xml and found all the feed info, which I was able to delete (I didn't delete the whole file).  Thanks!!

---

