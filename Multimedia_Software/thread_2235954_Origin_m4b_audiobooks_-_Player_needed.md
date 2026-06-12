---
title: "Origin m4b audiobooks - Player needed"
date: 2014-07-23
forum: Multimedia Software
---

### Post by achimneu on 2014-07-23
Hi - Need help

Before moving to Ubuntu bought a lot of audiobooks in m4b via iTunes....
Now I have not found any player on Ubuntu which does support this format due to codecs - DRM security....etc....
Neither is conversion a real propoer option although i tried sound converter but just one book takes ages....and we talk about a few GB in books.

Tried Juk, Rhythm, VLC etc...none does support m4b

Need help and advice how to get them running.

Cheers
Achim

---

### Post by Yellow Pasque on 2014-07-23
Does it take a long time to convert them with faad?
```
sudo apt-get install faad vorbis-tools
faad --stdio input.m4b | oggenc -q 5 - -o output.ogg
```

VLC supposedly can play the format, but I don't know about the DRM.

---

