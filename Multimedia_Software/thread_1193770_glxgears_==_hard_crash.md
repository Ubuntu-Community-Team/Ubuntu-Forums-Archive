---
title: "glxgears == hard crash"
date: 2009-06-21
forum: Multimedia Software
---

### Post by mjgoins on 2009-06-21
I just set up an amd64 machine with 9.04, and I'm getting an instant hard crash if I run glxgears.

I'm using the defaults (no xorg.conf file) for pretty much everything. No display manager, just running ratpoison from a startx command.

If it helps, it also hard crashes (screen instantly goes blank and system stops responding) when running the game alien arena.

Relevant info:

0 mjgoins@host:~ $ uname -a
Linux host 2.6.28-13-server #44-Ubuntu SMP Tue Jun 2 08:40:28 UTC 2009 x86_64 GNU/Linux


0 mjgoins@host:~ $ lspci | grep Radeon
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

---

### Post by Arup on 2009-06-22
You need to install the drivers either from repos or from ATI site.

---

