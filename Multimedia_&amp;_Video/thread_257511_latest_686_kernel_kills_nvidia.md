---
title: "latest 686 kernel kills nvidia"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by spiderworm on 2006-09-14
I updated my packages today, including the kernel.  Whoops!  The 2.6.15-26-686 kernel causes nvidia to crap out.  From dmesg:

nvidia: disagrees about version of symbol boot_cpu_data
nvidia: Unknown symbol boot_cpu_data

Somebody please fix, like, fast?

spiderworm

---

### Post by tseliot on 2006-09-14
read this:
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by spiderworm on 2006-09-14
That did it, thanks!  Man you guys are really on top of it around here!  Too bad I just looked in the wrong forum.

spiderworm

---

