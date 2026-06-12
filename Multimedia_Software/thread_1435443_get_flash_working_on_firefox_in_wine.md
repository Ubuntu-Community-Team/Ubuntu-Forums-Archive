---
title: "get flash working on firefox in wine?"
date: 2010-03-21
forum: Multimedia Software
---

### Post by higashi on 2010-03-21
there are some flash videos that i can't view because this site doesn't seem to be too compatible with linux, so i tried downloading firefox for window and opening with wine.
Now, the problem is that i can't get flash installed on my windows firefox :\
i saw a thread like this a while back but can't find it anywhere!
please help

---

### Post by hxcobd on 2010-03-21
It doesn't make any sense that a flash file would play in Windows but not in linux.

The issue is probably that you're using an old version of flash in linux. Update to Flash 10 in linux and I can virtually guarantee it'll work fine natively.

Also, post a link to the site in question and I'll verify it works fine in linux.

---

### Post by lovinglinux on 2010-03-21
See the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by phibxr on 2010-03-21
> **higashi said:**
> there are some flash videos that i can't view because this site doesn't seem to be too compatible with linux, so i tried downloading firefox for windoze and opening with wine.
Now, the problem is that i can't get flash installed on my windoze firefox :\
i saw a thread like this a while back but can't find it anywhere!
please help

Have you tried the following?

```
$ sudo apt-get install flashplugin-nonfree
```

The free version of the plugin doesn't play all content, as far as I know.

---

### Post by higashi on 2010-03-21
Flash is working fine on everything but this site, which works on windoze. my flash player is fine.
( l o c k e r z )

---

