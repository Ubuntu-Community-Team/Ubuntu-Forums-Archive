---
title: "Setting Mplayer as default media player."
date: 2009-03-28
forum: Multimedia Software
---

### Post by vasco.debian on 2009-03-28
Hi,

Any Idea How can I configure Mplayer as my default media player for
playing DVDs ?

Thanks & Regards,
Vasco

---

### Post by SteveDee on 2009-03-28
> **vasco.debian said:**
> Hi,

Any Idea How can I configure Mplayer as my default media player for
playing DVDs ?

Thanks & Regards,
Vasco

You can set the default for a given file type by right clicking the file > Properties > Open With.
Then select the application you want as default.

---

### Post by mc4man on 2009-03-28
for autoplay of dvd's upon insertion with mplayer the method would depend somewhat on what version of ubuntu your using and also on what your using as a frontend (the default gmplayer or smplayer, ect.

for 8.10 it's very straightforward, open up system ->  preferences -> file management -> media (if not in your preferences menu then enable thru edit menus or access with 
```
nautilus-file-management-properties
```

Or just insert a dvd and hold down the shift button, use the pop up to do below.

In the drop down for dvd video choose 'Open with other application'
For smplayer choose from list, if not there then use a custom command of simply smplayer (will work on multiple dvd drives, no need to change drive in smplayer options


For gmplayer don't pick from the list, use this as a custom command
```
gmplayer dvd://
```
Will only work from the default drive set in mplayer preferences

for 8.04 see here

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

