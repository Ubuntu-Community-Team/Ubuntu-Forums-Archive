---
title: "Firefox system crash issues (xorg)"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by nothinghead on 2007-07-01
I'm running firefox 2.0.0.4 on an AMD64 Fiesty. Sometimes, when changing tabs, loading a site, closing a tab, or closing the browser my system instantly restarts. I get booted to a black screen with text, a normal screen in the boot process (nothing apparently related to the error) and am back at my login screen within seconds.

Firefox's "error console" doesn't give me any hints. I've disabled greasemonkey but use the following extensions:
Adblock
Adblock Plus
Chatzilla
Conquery
Download Statusbar

Sometimes the error seems random, but I know that if I visit one specific website anytime during my browsing I will get the error when I either A) download a file or B) exit the browser.

Someone suggested that it was xorg that was crashing.  I don't know what to look for in the log files but I found the following in xorg.log.old

> Fatal server error:
Caught signal 11. Server aborting 

---

### Post by moore.bryan on 2007-07-02
[I]i've never had this issue, but a look on the linux forums yielded this:
[http://www.linuxquestions.org/questions/showthread.php?t=256896](http://www.linuxquestions.org/questions/showthread.php?t=256896)
perhaps a fix?
[/I]

---

### Post by nothinghead on 2007-07-02
Since I installed flashblock I haven't had a problem.  Though I do hope for the days when flash will work properly on an AMD 64 build.

---

