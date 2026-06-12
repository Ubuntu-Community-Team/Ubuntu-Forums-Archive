---
title: "[SOLVED] nVidia troubles with multiple screens"
date: 2008-10-13
forum: Multimedia Software
---

### Post by mewrei on 2008-10-13
Ok so I'm really having a few issues with a multiple monitor setup.  I'm using 2x22" monitors on an nVidia 8800GT and then a 17" monitor on an 8600GT.

I finally got it setup like I like it, but the problem is that there are some serious graphical slowdowns.  I cannot enable Compiz-Fusion either stating that "Composite extension is not available".

I'm running Ubuntu Hardy 8.04.1 32-bit with everything up to date.

Bellow is my current Xorg.conf file

**EDIT:** Nevermind, found out that the Xinerama and Composite X plugins don't work together and this is the cause of the problem.

---

### Post by HXn on 2008-10-16
Thanks, this probably saved me a lot of time trying to figure out what was wrong.

Just enable TwinView instead.

---

