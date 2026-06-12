---
title: "ATI 8.28.8 &amp; Radeon 9000 -- Google Earth locks up"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by diamond on 2006-09-10
I have a Dell Inspiron 600m (ATI Radeon FireGL 9000 chip) running Dapper. I recently installed the 8.28.8 version of the ATI drivers and release 4.0.1693 of Google Earth. Now, as near as I can tell the fglrx driver is working fine. The output of fglrxinfo is :

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

```

And glxgears gives me ~1300 FPS.

But when I try to start Google Earth, it just stops at the splash screen. I don't know how to get any sort of error log or debug output (/var/log/syslog shows nothing relevant), so I can't even begin to guess where the problem lies.

Any ideas? I miss my Google Earth terribly, and I'd love to have it back.

---

### Post by Paerez on 2006-12-13
I am in the same boat. Here is a good thread:
[http://www.ubuntuforums.org/showthread.php?t=241606](http://www.ubuntuforums.org/showthread.php?t=241606)
No solution yet, but watch it.

---

