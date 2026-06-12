---
title: "MPEG playback?"
date: 2009-03-17
forum: Multimedia Software
---

### Post by wobs on 2009-03-17
Sory if this is an obvious thing but - I can't get MPEGs to play in Kubuntu (I get sound only) using Kaffeine, MPlayer, Gxine etc.

Anone suggest what I could be missing?

---

### Post by Paul41 on 2009-03-17
Did you install the restricted extras package?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by wobs on 2009-03-17
No but I think I answered my own question - no codecs in /usr/lib/win32 ;)

Sorted now !

---

### Post by Paul41 on 2009-03-17
The restricted extras package will install all the codecs you need for audio and video.

---

### Post by wobs on 2009-03-17
Yes , I've run the command above and it all works fine now. Thank you for your help.

---

