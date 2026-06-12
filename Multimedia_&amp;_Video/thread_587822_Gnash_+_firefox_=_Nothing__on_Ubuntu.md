---
title: "Gnash + firefox = Nothing  on Ubuntu"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by underwater on 2007-10-23
I only get Gray boxes when viewing Youtube videos.  Any suggestions :*(

Gutsy + Gnash from the repos.  Mozilla plugin is installed.

---

### Post by bikeboy on 2007-10-23
Try this, I think it's what I needed to do when I tried gnash a little while back.

Close Firefox.
Create a plugins folder in your /home/user/.mozilla folder. Then create a symbolic link from there to the actual plugin.
```
cd ~/.mozilla/plugins
ln -s  /usr/lib/gnash/libgnashplugin.so libgnashplugin.so
```

Start Firefox and you should be right, if not check out the Preferences in Firefox to make sure it's using the plugin. If still nothing, tell us what you see when entering about:plugins in the address bar.

---

### Post by underwater on 2007-10-23
The link was already there.  I deleted it, marked gnash for complete removal, then installed it again and things seemed to have worked this time.  I'm not really sure why?  I gots nothings.  Thanks for the help though.

Underwater

---

### Post by bikeboy on 2007-10-23
No probs. I don't know what was wrong either, but as long is it works :)

---

