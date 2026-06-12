---
title: "OSS sound"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by hraposo on 2006-12-31
When I do the cedega teste it don't pass in OSS:
"oss sound failed"
Just in alsa
But the games have no sound.
Wthat's happen with OSS
How can I configure OSS sound?

---

### Post by pseudonym on 2006-12-31
Try this - ```
sudo apt-get install alsa-oss
``` It's the ALSA compatibility layer for OSS. Will allow OSS-supporting games to output sound via ALSA. Should also stop cedega complaining. :)

---

### Post by hraposo on 2006-12-31
already it's isntalled a version of alsa-oss

---

### Post by pseudonym on 2006-12-31
See [this post]("http://transgaming.org/forum/viewtopic.php?t=2057") at [transgaming]("http://transgaming.org/forum/").

---

### Post by hraposo on 2007-01-01
If I do: killall -9 esd when I'm going run cedega it's pass on oss teste and cedega have sound. How I stop esd of runing of startup debian?

---

### Post by pseudonym on 2007-01-01
There should be some way of doing it in your system properties/sound menu. some box you can check like 'disable esd at startup' (it says it at the bottom of that link I gave you, but for an older version of Gnome). Then, when you want to start esd again, uncheck the box, and log out/back in again.

I don't know the exact way to do this in the current Ubuntu version of gnome, because I don't use Gnome anymore.

---

