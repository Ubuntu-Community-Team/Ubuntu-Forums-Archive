---
title: "Special characters in subtitles"
date: 2009-12-31
forum: Multimedia Software
---

### Post by kl7mu on 2009-12-31
Hi, i'm using ubuntu in turkish. that's ok. but when i change my system language to english, in movies, my subtitles get corrupted. some characters in turkish like "&#351;,&#287; etc." are shown only as some silly symbols. but i wanna use my ubuntu in english language default, and also wanna watch the movies with turkish subtitle at the same time. is there any solution for that?

---

### Post by lovinglinux on 2009-12-31
You need to declare the languages in ~/.mplayer/config like this:

```
alang=English,eng,en
slang=Portuguese,por,pt
subfont-encoding="ISO-8859-1"
```

---

