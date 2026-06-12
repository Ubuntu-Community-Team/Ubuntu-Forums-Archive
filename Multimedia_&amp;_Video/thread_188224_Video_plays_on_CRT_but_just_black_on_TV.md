---
title: "Video plays on CRT but just black on TV"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2006-06-03
Hello all.  I'm running Dapper and using an ATI 9800 AIW card.  I have the fglrx drivers running with the "option "nodri"" to get past the boot-freeze problem.  I have a CRT and a TV , both set up in clone mode.

What I notice now is that when i play video, I see the video player on both screens, but on the TV I only see a black box where I see the video playing on the CRT.  Anyone know how to remedy this?

Thanks

---

### Post by barney_1 on 2006-06-04
Resolved:

Added this line to the device section of xorg.conf:
```
	Option	    "DesktopSetup" "mirror"
```

---

