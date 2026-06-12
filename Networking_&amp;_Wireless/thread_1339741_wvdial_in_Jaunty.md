---
title: "wvdial in Jaunty"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by Bunny Boy on 2009-11-27
wvdial works fine as long as I run it as root, i.e. *sudo wvdial*, however, when I try to just run *wvdial*, then I get this error:

[COLOR="Navy"]--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)
[/COLOR]

Do I need to *chmod* some other files to allow a regular user to run it?

---

### Post by Bunny Boy on 2009-11-27
Aha!  Finally got it to work:

[http://crunchbanglinux.org/forums/topic/3203/howto-wvdial-must-use-root-permission-fix-for-versions-804lts/](http://crunchbanglinux.org/forums/topic/3203/howto-wvdial-must-use-root-permission-fix-for-versions-804lts/)

---

### Post by inertz on 2009-11-27
Hi,

I think you can also use pppconfig for dial up.

---

