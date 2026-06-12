---
title: "[SOLVED] XviD support in Totem-xine suddenly broken"
date: 2008-09-30
forum: Multimedia Software
---

### Post by chezzo on 2008-09-30
Up until today playing xvid avi files in totem-xine worked absolutely perfectly, but it is now suddenly broken and I get the error message "Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies"

I have not knowingly done anything to bring this about... I've tried rebooting, reinstalling totem and all plugins, but with no success... Any ideas as to how I can find out the cause of the problem and fix it?

---

### Post by chezzo on 2008-10-16
bump?

I currently have totem-xine and totem-gstreamer installed at the same time, and use gstreamer to watch avi files... It's annoying though because I find that gstreamer isn't as good as xine, and sometimes gives me strange lagging effects in my videos.

I really want to use totem though, rather than mplayer etc, because it seems to be the only program that recognises my laptop's media buttons, and i like its shortcuts, like middle-clicking to pause.

---

### Post by warjowuch on 2008-10-23
Yup, exact same problem here existing a few days by now. Anyone else gotten to solution?

---

### Post by kostkon on 2008-10-24
For some reason your *catalog.cache* file got corrupted. Delete this file (keep a copy of it, just in case, you never know), it is in
```
~/.xine/catalog.cache
```
and the next time you run *totem-xine* it will be recreated. After this, you should be able to play XVIDs just fine.

---

### Post by chezzo on 2008-10-25
thankyouthankyouthankyouthankyou!

---

### Post by warjowuch on 2008-10-26
Whoo, thank you!
Weird though, that this could happen... but ok, now another answer for problems here in the forums...

---

