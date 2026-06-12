---
title: "nVidia 8600 SLI Problem"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by Awazah on 2007-08-02
Wow... I can't believe I haven't been able to find the answer to this online. Ubuntu is so widely documented, it makes troubleshooting a breeze :D

Anyway, I'm having somewhat of a weird problem... I just installed my second nVidia 8600GT, and bridged it with SLI, but for some reason it is not showing up in nvidia-settings. I used envy to install all the updated drivers and librarys, but still no avail.

I'm running x64, if that has anything to do with it.

Thanks!

---

### Post by tseliot on 2007-08-02
type:
```
sudo nvidia-xconfig --sli=Auto
```
and restart the Xserver

or try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

P.S. you can find the documentation of proprietary drivers on their respective websites.

---

