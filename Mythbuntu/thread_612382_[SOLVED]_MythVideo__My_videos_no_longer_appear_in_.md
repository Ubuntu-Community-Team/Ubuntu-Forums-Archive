---
title: "[SOLVED] MythVideo:  My videos no longer appear in frontend"
date: 2007-11-13
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-11-13
Strangely, I had just finished importing a DVD and attempted to view it when the screen when completely pink and the computer froze.  I had to cold reboot the machine.  Ever since then none of my videos appear in the gallery.  I've verified that the files are still located at /var/lib/mythtv/videos.  I can even double click on one through thunar and watch it in VLC.  

I've verified that the mythvideo folder is still /var/lib/mythtv/videos.  The video manager doesn't find any videos either.

Anybody got any ideas?

---

### Post by Meph1st0 on 2007-11-13
Just an FYI.  I've also gone into the file types section and made sure that none of them are set to ignore.

---

### Post by Meph1st0 on 2007-11-14
Does anyone have any ideas on this?  Is it possible that uninstalling mythvideo and then reinstalling it might fix it?

---

### Post by Meph1st0 on 2007-11-14
Update:  This appears to be related to the following bug:

[https://bugs.launchpad.net/ubuntu/+source/mythvideo/+bug/149370](https://bugs.launchpad.net/ubuntu/+source/mythvideo/+bug/149370)

I too had recently ran the update manager and since then I have been experiencing the same thing.

---

### Post by Meph1st0 on 2008-01-17
This was apparently fixed in a previous update.  I just recently updated and the problem has gone away.

---

