---
title: "Syncing htc desire using banshee"
date: 2010-05-12
forum: Multimedia Software
---

### Post by noteviljoe on 2010-05-12
Having some trouble syncing music to my HTC desire phone using Banshee.

The phone shows up fine as a 'HTC android phone'

However, the music is saved on the phone to a folder called /MP3 but Banshee doesn't see any of the music saved in that folder and when syncing puts music into a folder called /Music

Now Music would be a better folder name than MP3, however the phone's music application can't see the music saved in that folder.

Clicking on devise properties, then under advanced properties, gives me the music folder but doesn't let me change it :-( Edit - Preferences doesn't seem to give any joy either.

I can copy the music over using nautilus for now but I would like to be able to use Banshee.
 NUGE

---

### Post by noteviljoe on 2010-05-17
Nobody got an answer? :-(

---

### Post by u-foka on 2010-05-28
Hy!

Try to put a file named .is_audio_player into your sd card's root, that contains:
```
audio_folders=MP3/
```

---

### Post by noteviljoe on 2010-05-28
Thanks u-foka that seems to have done the trick :-)

---

