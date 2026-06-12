---
title: "vlc and qt4 problem"
date: 2010-02-13
forum: Multimedia Software
---

### Post by mahiyar on 2010-02-13
It is now almost half a day since I have tried solving this problem. VLC was working fine previously. Now when I try to open VLC I get the message 

> VLC media player 1.0.2 Goldeneye
[0x8c563e8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8d189a8] main generic error: no dialogs provider module matched "any"
[0x8d00998] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x8d00998] skins2 interface: skin: subX  author: Martin Poehlmann

Of course cvlc works. I have tried everything, reinstalling vlc, removing qt4 and again installing etc. etc. However the problem remains.

---

### Post by mc4man on 2010-02-13
To reset defaults inc. default qt interface

```
vlc --reset-config
```

or to set to qt4 (per use, not a default
```

vlc -I qt4
```

---

