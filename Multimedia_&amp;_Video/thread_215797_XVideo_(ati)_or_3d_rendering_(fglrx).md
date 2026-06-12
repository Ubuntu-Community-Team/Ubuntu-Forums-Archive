---
title: "XVideo (ati) or 3d rendering (fglrx)"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by MichaelPalin on 2006-07-14
Hi!,

I have installed Ati drivers through easyubuntu and fglrx through the tutorial in help.ubuntu.org, ([here]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")). For starters, I don't know what the difference is, but anyway, that's not the problem. The problem is that, if I choose ati driver through "dpkg-reconfigure xserver-xorg" I don't have 3Drendering, but if I choose fgrlx instead, I don't have xvideo, and I can't watch videos ok.

Any idea?, if you need more info tell what to do.

Thanks!

---

### Post by whatever on 2006-07-14
you can enable XVideo for fglrx by executing
```
sudo aticonfig --overlay-type=Xv
```
and restarting xorg

---

### Post by MichaelPalin on 2006-07-14
Done. Thanks a lot!

---

