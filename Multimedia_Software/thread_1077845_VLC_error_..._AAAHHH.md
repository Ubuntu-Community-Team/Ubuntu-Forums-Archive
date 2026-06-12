---
title: "VLC error ... AAAHHH"
date: 2009-02-22
forum: Multimedia Software
---

### Post by charlescarroll1 on 2009-02-22
I recently decided that it would look sweet to use a skin on VLC.  The skin I installed was [hx 1.1]("http://www.gnome-look.org/content/show.php/hx?content=86986") from Gnome-look.org.  Unfortunately, the skin was buggy as hell.  I was unable to revert back to the plain skin, or any other skin.  I deleted the buggy theme and now whenever I open VLC, I get an error message

> [COLOR="Red"]File reading failed:[/COLOR]
VLC could not open the file "/home/sysop/86986-hx_1.1_0.8.6.vlt"

I tried reinstalling VLC, and I still had the same error message!!!  I went into Synaptic Package Manager, and removed all traces of VLC, then reinstalled, and still get the same error.  What the hell is going on?  Someone help me stop crying!

---

### Post by mc4man on 2009-02-22
In a terminal
```
vlc --reset-config
```

(will come in handy

---

### Post by charlescarroll1 on 2009-02-22
Worked.  Thanks mc4man!

---

