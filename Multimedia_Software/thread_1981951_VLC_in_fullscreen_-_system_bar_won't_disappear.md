---
title: "VLC in fullscreen - system bar won't disappear"
date: 2012-05-17
forum: Multimedia Software
---

### Post by Yasashii on 2012-05-17
I've just installed VLC on my Xubuntu 12.04 and after going fullscreen the system bar at the top is still visible. That's quite annoying.

Anyone know how to fix this?

---

### Post by shantiq on 2012-05-17
maybe try   ```
metacity --replace

```
see if that shifts it

---

### Post by Yasashii on 2012-05-17
Could you explain what this command does exactly first? I'm a novice so I would rather not do things I don't know anything about.

---

### Post by shantiq on 2012-05-17
well   it   tends to fix that kind of thing



[U][URL="http://en.wikipedia.org/wiki/Metacity"][B]metacity  is a window manager
[/B][/URL][/U]

no worries as next time you reload it resets to what you usually have


if you use compiz


```
compiz  --replace
``` will   put it back   within the same session  



personally when anything does not go full screen properly i have found

**metacity  --replace**    to deal with that well

---

### Post by Yasashii on 2012-05-17
Umm... What about a permanent and less tricky solution?

---

