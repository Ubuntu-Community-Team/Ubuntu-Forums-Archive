---
title: "VERY slow connections to the internet"
date: 2005-01-29
forum: Networking &amp; Wireless
---

### Post by arnoct on 2005-01-29
I recently set up Ubuntu. First let me compliment the devteam, it's the first distro of Linux that I've found is usable right out of the box without any major tweaking. However, I'm having a minor problem.

When connecting to new websites, ubuntu can take up to 30 seconds to actually resolve the host. After that, it connects just fine. I have a 4mbit DSL connection, so the problem isn't with hardware (never had this problem before on windows.) I'm using a router, however I'm not having problems with the internet dying, I'm just having problems with it taking an inordinately long time to create new connections to  webpages and such. Do I have something misconfigured at all?

---

### Post by CowPie on 2005-01-31
[QUOTE=arnoct]I recently set up Ubuntu. First let me compliment the devteam, it's the first distro of Linux that I've found is usable right out of the box without any major tweaking. However, I'm having a minor problem.

When connecting to new websites, ubuntu can take up to 30 seconds to actually resolve the host. After that, it connects just fine. I have a 4mbit DSL connection, so the problem isn't with hardware (never had this problem before on windows.) I'm using a router, however I'm not having problems with the internet dying, I'm just having problems with it taking an inordinately long time to create new connections to  webpages and such. Do I have something misconfigured at all?[/QUOTE]
 Try to disable IPV6, I think it's under netwroking

OK I found out how:

nano -w /etc/modutils/aliases

de-hash the line:
    alias net-pf-10 off
    update-modules

From: [http://ubuntuforums.org/showthread.php?t=13414](http://ubuntuforums.org/showthread.php?t=13414)

---

