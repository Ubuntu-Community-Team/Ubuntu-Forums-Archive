---
title: "[SOLVED] Run a BASH script when I mount my iPod?"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by hackle577 on 2007-11-16
I tried adding ```
KERNEL=="sdb2", RUN+="/path/to/my/script.sh"
``` (where "sdb2" is my iPod) to "/etc/udev/rules.d/80-programs.rules", but it doesn't seem to be working.

I know there's a way to do this, but for the life of me I can't remember or find it...

---

### Post by hackle577 on 2007-11-17
Solved.

System > Preferences > Removable Drives and Media. I added the path to the script in the iPod's box and it works fine. I guess I thought it was more complicated than that...

---

