---
title: "Wrong time beginning of Mplayer time display on playing ts or m2ts file"
date: 2009-07-16
forum: Multimedia Software
---

### Post by shenjun5 on 2009-07-16
Wrong time beginning of Mplayer on playing ts or m2ts file

When playing ts or m2ts file, my mplayer's time-display not begins at zero second, but begins at 10:00 minutes, or 53 minutes, depending on the different ts/m2ts file. But the audio/video plays at the right beginning.

Therefore, audio/video right, time display wrong. The result is that the external subtitle loaded also begins at the wrong thread, causing a mis-syncronization.

However, when playing avi.,mkv files, mplayer gives the right time display. In other word, the time display begins at the right beginning.

Version of mplayer:2:1.0~rc2-0ubuntu19(jaunty)
Version of ubuntu: 9.04 jaunty
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1

I guess that mplayer doesn't analyze the beginning of ts/M2TS file in the right way. BTW, these ts/m2ts file plays at the correct beginning under windows os.

Does anybody know why? And how to fix this problem?

---

### Post by shenjun5 on 2009-07-16
Does anybody have any useful information?

---

### Post by Halbarad on 2009-09-02
Hi, I have exactly the same problem with a TS 1080P file, but I get the incredible amount of 12:39:30 just at the beginning. Cannot find any way of fixing it, though. :(

---

### Post by Nepherte on 2009-09-02
You're using a rather old version of mplayer. While it is supposedly to be the very latest release of mplayer, they continue to work on the svn version and don't put an effort in making another release for it. To install the latest mplayer, see: [http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

It might be fixed in the latest version, if not, report it on their mplayer-users mailing list: [http://www.mplayerhq.hu/design7/mailing_lists.html](http://www.mplayerhq.hu/design7/mailing_lists.html)

---

