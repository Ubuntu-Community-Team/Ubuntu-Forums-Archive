---
title: "Settings Apps as preferred in Dapper"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by lonelypauly on 2006-08-11
How would i set amaroK as my default audio player in dapper/gnome?

---

### Post by hopstah on 2006-08-11
this is an annoying bug, and one that i hope gets worked out in edgy.  the short answer is this - there is no way to change any setting to make amarok be the default player.  sure, you can make it open up when you double click an mp3, but what i assume you mean by default player is the one that opens when you push a media key on a keyboard.  is this right?

i'll assume it is, and give you this answer.  it's really not tough, but it's unnecessarily invasive, if you ask me.```
sudo ln -s /usr/bin/amarok /usr/local/bin/rhythmbox
```

this will make amarok open when you push the media key on your keyboard.

---

### Post by lonelypauly on 2006-08-11
That is exactly what i wanted...thank you so much!

---

