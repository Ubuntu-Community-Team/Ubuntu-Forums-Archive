---
title: "VLC Terminal"
date: 2010-10-23
forum: Multimedia Software
---

### Post by Shadow21 on 2010-10-23
I'm wanting to make a script that starts a song in VLC (when I turn on my computer) and replays it over and over so what command would I use to start a song in VLC?

---

### Post by mc4man on 2010-10-24
> what command (to start and repeat continuously

vlc -R /path/to/file

---

### Post by Shadow21 on 2010-10-24
Thanks!

Is there a way to make the VLC window automatically minimize?

---

### Post by mc4man on 2010-10-24
> Is there a way to make the VLC window automatically minimize?
sure - 
```
--qt-start-minimized
```
You can find most anything by running this, though dependimg on your version it may also have the annoying effect of resetting
 your vlc config to the orig. defaults (has been fixed in vlc 1.2+

vlc -H

---

### Post by Shadow21 on 2010-10-24
> **mc4man said:**
> sure - 
```
--qt-start-minimized
```
You can find most anything by running this, though dependimg on your version it may also have the annoying effect of resetting
 your vlc config to the orig. defaults (has been fixed in vlc 1.2+

vlc -H

Thanks! :)

---

