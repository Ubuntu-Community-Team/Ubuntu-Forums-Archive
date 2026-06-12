---
title: "low FPS - Intel x3100 GM965, Intrepid 8.10"
date: 2009-03-11
forum: Multimedia Software
---

### Post by IQRules on 2009-03-11
I think this is an Intel video card driver issue.
Where to get the right APT package/patch on this slowness?

$ glxgears
1884 frames in 5.0 seconds = 376.637 FPS
1900 frames in 5.0 seconds = 379.877 FPS
1895 frames in 5.0 seconds = 378.817 FPS
^C
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

$ uname -a
Linux os64 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

---

### Post by jongkind on 2009-03-15
This read gives intersting news on the value of glxgears:
[http://qa-rockstar.livejournal.com/7869.html]("http://qa-rockstar.livejournal.com/7869.html")

---

