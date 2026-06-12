---
title: "How to get rid of MYTH"
date: 2011-01-26
forum: Mythbuntu
---

### Post by Henk30 on 2011-01-26
I  uncarefully installed "Myth".
Now I get a Dos-like screen but I do not know the commands. I  like to have back  my Ubuntu with the Window-appearance, because I even can not reach my E-mail anymore.
Who can tell me how to get rid of "Myth" ? Preferally in Dutch.

Thank you for thinking about it.
Henk 30

---

### Post by dsbw on 2011-01-26
Sounds like you need to reinstall or maybe just restart X. What happens if you:

/etc/init.d/gdm start

? (Sorry for the non-Dutch.)

Groetjes

---

### Post by nickrout on 2011-01-26
```
sudo aptitude remove mythbuntu-desktop
```

---

