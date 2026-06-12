---
title: "Banshee freezes up"
date: 2010-11-15
forum: Multimedia Software
---

### Post by nmyrick on 2010-11-15
I just started having a problem tonight with Banshee.  Whenever I click on some of my playlists, Banshee crashes.  Can anyone tell me where I would find the error log for this so that I can fix it?

---

### Post by s3MA00RRNY on 2010-11-16
find . -iwholename '*ban*log*'

~/.config/banshee-1/log

---

### Post by nmyrick on 2010-11-16
Thanks, I just figured out the fix.  I had to delete the banshee database.  I had to go into /home/<username>/.config/banshee-1 and delete the banshee.db file.  Then restart banshee and rebuild my playlists.

---

