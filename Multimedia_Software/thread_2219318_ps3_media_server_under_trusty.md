---
title: "ps3 media server under trusty"
date: 2014-04-23
forum: Multimedia Software
---

### Post by ray field on 2014-04-23
when I run apt-get all of PS3 Media Server's dependencies seem to have have been resolved, but in fact tsmuxer and mencoder do NOT work here -- while ffmpeg DOES (maybe because I installed gstreamer0.10-ffmpeg a la [http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html))

while Trusty was still in beta, it made some sense that the multimedia repositories were unsettled. but now I'm a little bit concerned and wonder if there are workarounds that can be used within PMS or in Ubuntu -- or just even if anyone understands exactly what the problems is/are.

---

### Post by SeijiSensei on 2014-04-23
I installed mencoder on my 14.04 machine just the other night from the standard repositories.  Did you try using "sudo apt-get install mencoder" from the command prompt, or selecting it in a GUI package manager?

I know nothing about tsmuxer, but you can try the same approach for that.

---

### Post by ray field on 2014-04-23
thanks for the reply. mencoder is installed, the latest version.

tsmuxer comes with PMS, and is marked executable (in the PMS install folder). I suspect its dependencies are unfulfilled -- running videos with it produces loud static, though the video works. I should say, PMS has worked for me since around Oneiric.

---

