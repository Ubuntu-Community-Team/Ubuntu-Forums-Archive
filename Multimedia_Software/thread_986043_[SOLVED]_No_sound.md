---
title: "[SOLVED] No sound"
date: 2008-11-18
forum: Multimedia Software
---

### Post by The Midnight Coder on 2008-11-18
I did a command line installation from my xubuntu alternate cd and then added xorg, icewm later on and now whenever i try to play any music in audacious there is no sound

any suggestions on what to do?

---

### Post by The Midnight Coder on 2008-11-18
I managed to fix it by installing the package alsamixergui and setting all the speaker icons to on.

```
sudo apt-get install alsamixergui
```

And I had thought by setting the volume to max using alsamixer was enough....hope this helps someone in the future...

---

