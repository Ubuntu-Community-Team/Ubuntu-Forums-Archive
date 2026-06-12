---
title: "Fatal Error: No Screens Found"
date: 2011-02-15
forum: Multimedia Software
---

### Post by rcuswalk on 2011-02-15
I just installed Maverick on a brand new system last Saturday. Everything worked, except dual monitors, so I activated the proprietary ATI/AMD driver. That allowed the dual monitors to work, except that it put a little "AMD unsupported hardware" watermark in the lower right-hand side of each screen. After a day or two, I decided to go back to the default driver while trying to figure out how to avoid the watermark. I assumed that when I deactivated/removed the proprietary driver that it would automatically switch back to the default. Instead, my computer now boots to TTY1, and when I try to install xserver.xorg, etc., I get a lot of error messages, like "No screens found" or "Screens found, but configuration is unusable," etc. The same messages show up in the logs.

Can anyone help me get back to a useable desktop display? At this point, I don't care which one. Perhaps the proprietary would be easiest since it seems to be holding my system hostage, but either one would work.

---

### Post by jerrrys on 2011-02-16
is this what you need ?

[ATTACH]183651[/ATTACH]
**[B]sudo apt-get install xserver-xorg-video-ati**[/B]

---

