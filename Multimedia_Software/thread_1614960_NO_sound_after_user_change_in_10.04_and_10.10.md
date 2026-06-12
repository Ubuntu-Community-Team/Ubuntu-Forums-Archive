---
title: "NO sound after user change in 10.04 and 10.10"
date: 2010-11-06
forum: Multimedia Software
---

### Post by Thorndog on 2010-11-06
Ever since I upgraded to 10.04 and now again in 10.10 I have no sound after changing users. The other user has user privileges for sound.

---

### Post by lidex on 2010-11-06
I believe that is default behavior for pulseaudio. Try starting it as the new user, either
```
pulseaudio
or pulseaudio -D
```
in a terminal.

---

