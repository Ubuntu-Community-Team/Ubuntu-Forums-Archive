---
title: "smplayer cursor reappears"
date: 2010-01-20
forum: Multimedia Software
---

### Post by UnsafeData on 2010-01-20
Cursor reappears and disappears every once in a while while playing a video fullscreen in smplayer. I dont move my mouse. Not a mouse problem, I've definitely checked..

---

### Post by rvm4000 on 2010-01-20
It's a problem caused by a patch added to mplayer by the ubuntu maintainers.

Easy way to avoid it: uncheck the option "disable screensaver" in preferences -> general -> video.

---

### Post by UnsafeData on 2010-01-20
Thanks, worked.

---

### Post by masque7 on 2010-08-05
> **rvm4000 said:**
> It's a problem caused by a patch added to mplayer by the ubuntu maintainers.

Easy way to avoid it: uncheck the option "disable screensaver" in preferences -> general -> video.
Then how are we supposed to stop the screensaver from starting when watching video?

---

### Post by Linuxforall on 2010-08-06
Best is to add mplayer and smplayer ppa from the developer of smplayer to get updates mplayer and smplayer, this one has no issues.

---

### Post by masque7 on 2010-08-06
For anyone that wants the ppa it's
**```
sudo add-apt-repository ppa:rvm/smplayer
```**

---

