---
title: "Taking screenshot with [Fn] + [Prnt Scrn]  = Power OFF"
date: 2010-07-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2010-07-17
Worked in 10.04 and before, in 10.10 (Gnome) the screenshot taking key combination now does instant power down. gnome-screenshot still works.

---

### Post by kyleabaker on 2010-07-18
> **TDK800 said:**
> Worked in 10.04 and before, in 10.10 (Gnome) the screenshot taking key combination now does instant power down. gnome-screenshot still works.

This is a known issue and has been present for a while in Ubuntu 10.10 now. There is another thread discussing this or something very similar. I've seen this happen myself.
[http://ubuntuforums.org/showthread.php?t=1525386](http://ubuntuforums.org/showthread.php?t=1525386)

It is apparently a kernel bug, thats probably why you're getting a crash/power off. The report says a fix has been released already. Have you installed updates recently?
Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257)

---

### Post by MacUntu on 2010-07-18
That's a different issue. Alt+Print doesn't seem to generate a key code anymore (eg. I cannot set a shortcut to use that combo).

---

### Post by kyleabaker on 2010-07-18
> **MacUntu said:**
> That's a different issue. Alt+Print doesn't seem to generate a key code anymore (eg. I cannot set a shortcut to use that combo).

If I understand correctly, this thread is about [Fn]+[Print Screen], meaning its a laptop where [Fn] is just an extra step for a regular Print Screen. Not Alt+Print Screen. There does seem to be a bug with Alt+Print Screen, but I don't think @TDK800's problem is dealing with Alt.

I've actually seen it crash my computer pressing Print Screen in the past, before updates. However, that bug may be different from the exact issue. If thats the case, the @TDK800 you should file a new bug report if its still crashing.

---

### Post by mc4man on 2010-07-19
As part of that bug  (at least i thought), once you used Alt then the print (PrtSc here) became non-functional or worse.

Now that it has been 'fixed' print seems to work fine on normal keyboards but Alt+PrtSc does nothing.

(here I made a panel launcher w/ command of gnome-screenshot -w -d 3 -b
to replace the function

If there is an issue with [Fn] + [Prnt Scrn] and you're updated I'd file a new bug

Edit:though on my laptop Prnt Scrn is the 'default', using Fn would mean SysRq

---

