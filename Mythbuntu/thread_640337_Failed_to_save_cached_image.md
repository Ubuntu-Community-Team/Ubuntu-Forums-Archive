---
title: "Failed to save cached image"
date: 2007-12-14
forum: Mythbuntu
---

### Post by NickGray on 2007-12-14
Using Ubuntu 7.10 and MythTV 0.20.2.
I think **my permissions for the folder themecache** are messed up. Can anyone help me? I am getting a ton of "Failed to save cached image messages whenever I change resolutions or themes. For example,

```
2007-12-13 12:38:49.374 Failed to save cached image: /home/nick/.mythtv/themecache/Retro.1024.768/unknown.png
2007-12-13 12:38:49.378 Failed to save cached image: /home/nick/.mythtv/themecache/Retro.1024.768/uparrow.png
2007-12-13 12:38:49.541 Failed to save cached image: /home/nick/.mythtv/themecache/Retro.1024.768/video-frame.png
2007-12-13 12:38:49.567 Failed to save cached image: /home/nick/.mythtv/themecache/Retro.1024.768/webpage.pn
```

CHMOD'ing the directory to **777** fixes the problem, but I would have to do that for every theme and every resolution.

Any advice?

---

### Post by NickGray on 2007-12-14
Bump... any CHMOD advice?

---

### Post by Caysho on 2009-02-20
I get this on mythbuntu 8.10

```

==> /var/log/mythtv/mythfrontend.log <==
2009-02-20 18:11:23.381 Failed to save cached image: /home/mythtvuser/.mythtv/themecache/Mythbuntu-8.04.1920.1080/news-info-bg.png
2009-02-20 18:11:23.385 Failed to save cached image: /home/mythtvuser/.mythtv/themecache/Mythbuntu-8.04.1920.1080/next_button_off.png
2009-02-20 18:11:23.388 Failed to save cached image: /home/mythtvuser/.mythtv/themecache/Mythbuntu-8.04.1920.1080/next_button_on.png

```

~/.mythtv/ needs to be read/write by group mythtv.  A default install has it read only.
[Bug report submitted]("https://bugs.launchpad.net/bugs/332736").

---

