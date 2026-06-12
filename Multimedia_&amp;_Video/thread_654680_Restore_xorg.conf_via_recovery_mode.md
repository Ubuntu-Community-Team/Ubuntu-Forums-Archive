---
title: "Restore xorg.conf via recovery mode"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by drazabyss on 2007-12-31
I want to restore from a backup that I have - not to a default.  From recovery terminal, what is the easiest way to do this?  I am a complete linux n00b.  Love ubuntu so far, but cracked up my xorg.conf while trying to install my ATI GFX driver.

Additional:

Very simple question, but, again, I am a n00b to LINUX and all parts thereof:  How does one change between dirs in terminal?  'cd ect' for example does not work although 'dir' shows ect as a dir in the folder I am currently in.  I know I am not using DOS and that it is a format error, I just don't even know anything as easy as what the format is.

TIA

---

### Post by taurus on 2007-12-31
```
cd /etc/X11
cp **backup_file** xorg.conf
```
_Replace_ backup_file with the actual name of the file from your backup.

---

### Post by drazabyss on 2007-12-31
I love this place.  Thanks!

---

### Post by nick_h on 2007-12-31
> How does one change between dirs in terminal? 'cd ect' for example does not work
cd should work.  Remember that linux is case sensitive.

---

