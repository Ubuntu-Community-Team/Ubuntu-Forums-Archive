---
title: "Quick ALSA question"
date: 2008-08-25
forum: Multimedia Software
---

### Post by Tarmael on 2008-08-25
I play a lot of PSX games (using PCSX) and often when I'm finished ALSA has been grabbed by the game I closed down and thus a restart (or sudo shutdown) is needed to fix it.

Any way to just restart the ALSA?

---

### Post by Stemp on 2008-08-25
```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by Tarmael on 2008-08-29
Thanks heaps.

I'll try that next time.

---

