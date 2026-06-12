---
title: "Mplayer plugin working in galeon but not firefox"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by Caligula on 2007-06-10
I have a weird problem with the mplayer plugin.

All in all it works, but in certain websites, such as stage6.divx.com it works in galeon, but when i'm using firefox it's acting as if I don't have it installed.
Is it possible that it's got something to do with the format(divx)? because in other websites it does work...

Any input will be welcome.

Thanks,
Josh

---

### Post by reclusivemonkey on 2007-06-21
What does the output of 

```
ls /usr/lib/firefox/plugins/

```

show?

---

### Post by Gremlinzzz on 2007-06-21
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
worked for me

---

