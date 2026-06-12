---
title: "Nvidia OpenGL X crash"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by GameGod on 2006-11-13
Hey guys,

I've a doozy of a problem that I can't quite seem to fix. Whenever I launch an OpenGL application, Xorg crashes (drops me back to commandline, and when it tries to fire up GDM again, my PC freezes... unless I stop GDM in time).
I thought I had OpenGL working fine before with the Nvidia 9625 beta drivers, but I'm not sure if it's worked since I upgraded to the 9629 drivers.

When Xorg dies, the last lines are:
```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: [0x81fcfc0]

```

I thought maybe it had something to do with "libxorg-sched-yield-hack0", but I don't know anymore. (Adding the package changes the backtrace slightly when Xorg dies.)
Also, OpenGL used to work just fine on Edgy, but I believe an update from that repository with the updated Nvidia drivers in linux-restricted-modules broke it...

If anyone can point me in the right direction here, it'd be greatly appreciated!

Thanks!

---

