---
title: "[SOLVED] How do I watch .iso movies in VLC."
date: 2008-10-07
forum: Multimedia Software
---

### Post by u-slayer on 2008-10-07
When I try to double click on .iso dvd movies in nautilus, VLC plays the .vob files sequentially without any navigation structure. It also creates bogus audio tracks. 

If I start VLC first and click File->Open, the movies play fine.

What command line should I set nautilus to use to open .iso dvd movies properly?

---

### Post by mc4man on 2008-10-07
right click on an iso -> properties -> open with -> add -> use a custom command. use this
```
vlc %f
```

Also it's better overall to use the above as vlc's launch command. Go right click on applications -> edit menus. Highlight sound & video, on right side right click on vlc -> properties and use above as the command (better than vlc %U

If you change vlc's launch command you probably don't need to set a custom file association  (unless you set it before using a custom command (vlc %U

---

### Post by ddixonr on 2008-10-07
What exactly does that switch do?

---

### Post by mc4man on 2008-10-07
It's having vlc access a single file name instead of a URL (or group of.
In the case of dvds all the basic info is in VIDEO_TS.IFO so that's what you want accessed, not all the .IFO's (to start at least

see here - 2/3 down page
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

---

