---
title: "HP Mini 110 broadcom wireless?"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by ibootindos on 2010-10-23
I installed Ubuntu Netbook on my windows xp machine, a HP Mini 110 with a broadcom wireless card, I installed using Wubi. The wireless on the ubuntu side isn't working and I can't plug into a physical line, how do I fix this?

---

### Post by ibootindos on 2010-10-23
Seriously, help! lol

---

### Post by ibootindos on 2010-10-23
Ok, so I found the driver I need, but I need to build it from a tar.gz file, which I can't do without the headers and tools, which I can't get unless I'm connected to the internet, which I'm not because my wireless drivers aren't working... does anybody know a work around for this?

---

### Post by ugm6hr on 2010-10-23
Confirm your wifi card with:
```
lspci
```

After which, it should be possible to get it done. I had to do something similar for 10.04, but just used a cable for 10.10. A bit of fiddling to modify the advice here should hopefully work:
[http://ubuntuforums.org/showthread.php?p=9263039#post9263039](http://ubuntuforums.org/showthread.php?p=9263039#post9263039)

---

