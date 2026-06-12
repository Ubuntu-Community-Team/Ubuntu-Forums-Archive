---
title: "[Edgy Eft] Audacity won't load"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by Elrohir on 2007-04-24
Whenever I open Audacity I get this error message:```
There was an error initializing the audio player i/o layer. 
You will not be able to play or record audio.

Error: Host error.
```
any ideas for this? I thought it might be because of permissions so I tried
```
gksu audacity
```with no success...

---

### Post by solar george on 2007-04-24
Have you got the alsa-oss packages installed?

---

### Post by Elrohir on 2007-04-25
> **solar george said:**
> Have you got the alsa-oss packages installed?yes, no go...

---

### Post by solar george on 2007-04-25
Have you tried closing all other sound applications?

---

### Post by Elrohir on 2007-04-25
all of them are closed... thought that also might be the problem, so I reboot and when I just logged in and run Audacity... same...

---

### Post by solar george on 2007-04-26
Try going into synaptic and marking audacity for complete removal, applying that and then reinstalling.

---

### Post by Elrohir on 2007-04-28
> **solar george said:**
> Try going into synaptic and marking audacity for complete removal, applying that and then reinstalling.
interesting... that worked... thanx!

---

