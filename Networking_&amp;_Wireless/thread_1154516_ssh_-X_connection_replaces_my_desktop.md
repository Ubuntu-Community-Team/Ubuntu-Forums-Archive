---
title: "ssh -X connection replaces my desktop"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by dark_mage93 on 2009-05-09
hi,
I started an "ssh -X" connection to a school server and everything was fine until I ran "nautilus . &"

that command replaced my local desktop with the school account desktop. I used "ps -fu username" and "kill -9" to kill all processes that were running remotely, and that killed the icons, but the desktop on my local computer still has the desktop background of my remote account. weird. I don't know how to to fix this, other than logging out of my local account and logging back in. everything is fine then until I run "nautilus" again remotely.

weird.
help please? how do I disconnect cleanly from a remote server?

thanks!

---

### Post by ad_267 on 2009-05-09
I'm not sure about disconnecting, but try running "nautilus --no-desktop" next time.

---

