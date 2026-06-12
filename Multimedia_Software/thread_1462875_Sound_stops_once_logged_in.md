---
title: "Sound stops once logged in"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Mickeysofine1972 on 2010-04-26
Hi All

I'm having problems with my sound not working after I have logged in.

I hear a login sound fine, but after I login there no sound and the app under system > preferences > sounds dies when I press the test buttons

Anyone know what might be happening?

EDIT: Ok I managed to fix this by doing:

```
sudo alsa force-reload
```

But it remains to be seen if I'll have to do this each time I restart

---

