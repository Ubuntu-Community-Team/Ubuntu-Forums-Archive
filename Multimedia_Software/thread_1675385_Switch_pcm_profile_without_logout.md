---
title: "Switch pcm profile without logout"
date: 2011-01-25
forum: Multimedia Software
---

### Post by kresnik7 on 2011-01-25
Below is my ~/.asoundrc, which is working as desired.  I can change the "pcm.!default" value, log out then back in, and it takes effect as desired.

How can I switch the profiles without logging out?

```

pcm.mono_right {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.1 1
   ttable.1.1 1
 }

pcm.mono_left {
   type route
   slave.pcm  "cards.pcm.default"
   ttable.0.0 1
   ttable.1.0 1
 }

pcm.!default pcm.mono_right
#pcm.!default pcm.mono_left

```

---

### Post by kresnik7 on 2011-01-26
Partial solution from [[COLOR="Blue"]Ivan[/COLOR]]("http://www.ivankristianto.com/os/ubuntu/tips-solving-ubuntu-sound-problem-without-restart/440/")
[INDENT]1. lsof | grep pcm
2. Kill each process listed
3. /etc/init.d/alsa-utils restart
4. Restart each killed application
[/INDENT]
This doesn't work 100%, and isn't pretty.  Other solutions would be appreciated.

---

### Post by Jose Catre-Vandis on 2011-01-26
Try:
```
sudo alsa force-reload
```

---

### Post by kresnik7 on 2011-01-26
Thanks Jose, that's much cleaner, but this has the same problem as Ivan's solution: killed applications.

Still looking for an alternate solution if anyone has one, which won't make me quit everything.

---

