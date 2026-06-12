---
title: "a fun way to play a radio station ?"
date: 2015-03-28
forum: Multimedia Software
---

### Post by shantiq on 2015-03-28
if you like to have one radio station to start fast from your desktop but not automatically how about this way:

[ATTACH=CONFIG]260946[/ATTACH]

save text to ~/Desktop 

and to control pause/play with Systems Monitor Stop Process/ Continue Process

ps mpv my favourite for this altho cvlc good too

EDIT


** if you want to test use this station instead as one above can be temperamental **and of course link to your own icon

```
[Desktop Entry]
Name=klassisk
#http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h
Exec=mpv http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h
Type=Application
StartupNotify=true
Icon=/home/shantiq/Pictures/vlc_icons/nrk.png
```

---

### Post by mc4man on 2015-03-28
I'd probably add --force-window for mpv to gain control + get icy data, ect. in window deco
ex.
Exec=mpv --force-window  [http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h](http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h)

---

### Post by shantiq on 2015-03-29
nice idea mc  maybe better than dicking around with Systems Monitor altho same effort really: one click :] but no data with SMonitor

---

