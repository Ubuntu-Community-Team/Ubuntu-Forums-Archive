---
title: "Glitchy audio after being &quot;Suspended&quot;"
date: 2013-04-11
forum: Multimedia Software
---

### Post by Tinsnip on 2013-04-11
I'm running Ubuntu 12.10 with kernel version 3.7.0

Everythig with my multimedia works great, except after I close or suspend my laptop.  Upon waking back up, my computer has glitchy audio on everything from games, to YouTube and Hulu, and requires a reboot to work properly again.  I'm hoping that this will be solved with the release of 13.4 in the next couple weeks, but does anyone know why this may be happening and what I can do about it?

---

### Post by mmstick on 2013-04-11
I haven't experienced that with my laptop on ubuntu 13.04, or ubuntu 12.10.

---

### Post by Toz on 2013-04-11
After resume, try reloading alsa:
```
sudo alsa force-reload
```

If that works, we can script it to happen automatically on resume.

---

### Post by Tinsnip on 2013-04-16
bummer, the command "sudo alsa force-reload" did nothing for me.

---

### Post by Tinsnip on 2013-04-16
> **Tinsnip said:**
> bummer, the command "sudo alsa force-reload" did nothing for me.

it looks like there's a little confusion between my 12.10 version and updating to the 3.7.0 kernel (so my wireless card would work).  I'm pretty sure that when I update to 13.04 everything will smooth out.

---

