---
title: "First WiFi connection (after the login) very slowly"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by joined on 2009-05-21
Hi to all,

I'm a really happy owner of a fresh Ubuntu 9.04 but I have a little problem.

When I log into my account the WiFi connection goes online very, very slowly (sometimes after about 2-3 minutes), but some other times goes online instantly (after about 2-3 seconds).

I have a dual-boot system (with XP that I rarely use) and when I use XP the WiFi connection goes online instantly.

What could be the problem on Ubuntu?

Some additional Info:
My WiFi lan is hidden (doesn't has a public SID) and use a WPA/WPA2 key.

Thanks to all!

---
Best regards...

Fabio Dell'Aria.

---

### Post by superprash2003 on 2009-05-21
login to my account?? are you talking about a mail account?? is this a DSL connection?

---

### Post by joined on 2009-05-21
Hi,

I intend when I logged to my Gnome account.

---

### Post by NilsE on 2009-05-21
Seems like a number of people are noticing the same thing, including me.  See the following thread which discusses it a little more but no real fix to Network Manager.

[http://ubuntuforums.org/showthread.php?t=1152562](http://ubuntuforums.org/showthread.php?t=1152562)

---

### Post by NilsE on 2009-06-01
Based on another problem (periodic dropouts) I enabled backports in Software sources (actually was already enabled) and installed 

linux-backports-modules-jaunty 

and now it connects almost immediately as it did in Intrepid.

---

