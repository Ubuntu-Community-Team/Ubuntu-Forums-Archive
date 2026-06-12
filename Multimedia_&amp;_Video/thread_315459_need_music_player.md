---
title: "need music player"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by Hairy_Palms on 2006-12-09
hey all, im on a quest for a command line audio player with a difference, it neeeds to have a pause command, ive tried mplayer it doesnt and ive tried mpg123 as far as i can see neither let you pause with a command any ides? thx

---

### Post by pete on 2006-12-09
mpg123 does let you pause, but only if you start it with the "-C" or "--control" switch (e.g., "mpg123 -C <filenames>").  That tells it to enable terminal control keys.  Once you've done that, hitting the 'S' key during playback will do the trick (the rest of the control keys can be found on the mpg123 man page).

You could also check out MOC ([http://moc.daper.net/)](http://moc.daper.net/)), which is fairly feature-rich as command-line music players go.

---

### Post by Hairy_Palms on 2006-12-09
noo i mean  i want to be able to pause with a _command_ not a key sequence tried moc, but couldnt get it to work, once compiled it just hangs when i run in the terminal

---

### Post by Hairy_Palms on 2006-12-10
ive found my happy place with xmms2d :) does everything with commands, :)

---

