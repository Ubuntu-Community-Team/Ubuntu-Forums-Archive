---
title: "MuseScore will not write to disc"
date: 2010-04-16
forum: Multimedia Software
---

### Post by Mrsongs on 2010-04-16
I'm running MuseScore in Karmic; thanks to this forum, I've gotten it to play midi; it reads files fine, but it doesn't seem to want to write to disc! Has anyone else encountered this problem?:confused:

---

### Post by johngreth on 2010-04-20
It can probably save files, just not create new ones. Try running:
```
gksudo mscore
```
to give it full permissions to save files. Then it should be able to read and save over that file even in normal mode. I also have solutions to other problems on [my blog]("http://johngreth.com/blog/?p=332") if you need it.

---

