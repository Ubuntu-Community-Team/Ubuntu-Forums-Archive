---
title: "Ubuntu not recognizing MP3 player"
date: 2010-03-14
forum: Multimedia Software
---

### Post by Tao Xuin on 2010-03-14
I have a Sansa Fuze MP3 player but when I connect it to my computer Ubuntu doesn't recognize that there is anything connected. When I connect it to my computer nothing happens, like nothing is even plugged in. How do I install it or get it to recognize the MP3 player?

---

### Post by Slantzalot on 2010-03-16
I have the exact same problem. I'm assuming nobody here knows or it's just a very noobish question. Anybody?

---

### Post by Chronon on 2010-03-16
Neither of you mentioned what version of Ubuntu you're using.  I had this problem a while ago due to libgphoto2 wrongly identifying my devices as MTP even when in MSC mode (i.e. acting as UMS devices).  I haven't had any problem recently in Karmic, though.  My devices get auto-mounted and appear in my file browser as expected.

---

### Post by Slantzalot on 2010-03-17
> **Chronon said:**
> Neither of you mentioned what version of Ubuntu you're using.  I had this problem a while ago due to libgphoto2 wrongly identifying my devices as MTP even when in MSC mode (i.e. acting as UMS devices).  I haven't had any problem recently in Karmic, though.  My devices get auto-mounted and appear in my file browser as expected.

Oops sorry, using Ubuntu 9.10, not sure about Karmic or whatever because I'm new to all of this. If it helps I got it from this link [http://www.ubuntu.com/GetUbuntu/download]("http://http://www.ubuntu.com/GetUbuntu/download"), sorry if that doesn't help. Any suggestions?

---

### Post by Chronon on 2010-03-17
I am also using 9.10 (codename Karmic Koala) but with KDE.  Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998)

It is strange because it appears that most people claim that the 9.10 packages resolved the problem for them, however some people are experiencing this problem afresh with installing 9.10.  Anyway, you can investigate that bug report and see if any of the workarounds work for you.  If they don't then it would be good to describe your situation with as much detail as possible there.  

Unfortunately, due to the inconsistency with this I can't really offer definitive help on making it work properly.  At one point I simply moved (renamed) the whole [FONT="Courier New"]/usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi[/FONT] to prevent libgphoto from detecting my devices (I don't ever use MTP on my system, so this is fine for me).  That was on 9.04.  I don't have this problem any longer on a fresh install of 9.10.

edit: I'm not sure that this workaround is still applicable in Karmic.  I seem to recall that HAL is largely deprecated in Karmic.

---

