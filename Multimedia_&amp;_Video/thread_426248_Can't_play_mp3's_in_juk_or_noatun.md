---
title: "Can't play mp3's in juk or noatun"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by duns0014 on 2007-04-28
Even though I can play them in kaffeine and others.  I can play ogg files in juk and noatun though.  It doesn't give me any errors or even any messages when launched from the terminal.  It just doesn't play them.

---

### Post by duns0014 on 2007-04-28
I have a clue.  I think that juk and noatun both use aRts, while kaffeine and others do not.  If this is true, I've helped isolate the problem.  But why would aRts play ogg and not mp3?

---

### Post by duns0014 on 2007-04-29
No one?  Nothing?

---

### Post by alan.clements on 2007-06-23
There is a simple fix:
```
sudo apt-get install libarts1-mpeglib
```

cheers! :D

---

