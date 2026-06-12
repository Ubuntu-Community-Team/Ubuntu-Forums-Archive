---
title: "Question about Hulu Desktop"
date: 2009-10-14
forum: Mythbuntu
---

### Post by bcg30506 on 2009-10-14
Does anyone know of a way to hide the mouse cursor in Hulu Desktop?  I run it from mythfrontend in my living room system using a remote control and have no mouse in there.  The cursor is near the center of the screen and remains the entire time the shows play.  If I plug in a mouse or VNC into the box I can move the cursor off to the side of even just bump it, which then triggers Hulu to hide it after a few seconds of inactivity.  This kills the WAF however.  I do not know where to post issues on their web site.

---

### Post by bcg30506 on 2009-10-14
I think I answered my own question with the help of the Hulu discussion board I found via Google.  They mentioned using a utility called unclutter.  I installed it with sudo apt-get install unclutter.  Then did the following:

It may not be the "preferred" method, but it works and might help other MythTV/Hulu users out there.   I created a small little script and made it executable in /usr/local/bin called runhuludesktop which looks like:

#!/bin/bash
export DISPLAY=:0.0
unclutter -idle 1 &
/usr/bin/huludesktop
pkill -f unclutter

So it only runs unclutter while huludesktop is running, which is the only time I need it.  In my MythTV menus where Hulu gets run, I changed the command from huludesktop to runhuludesktop and restarted the frontend so the new menu takes effect.

BTW, here is the board for discussing the Hulu Desktop app:

[http://www.hulu.com/discussions/19](http://www.hulu.com/discussions/19)

---

### Post by uncle hammy on 2009-10-14
I think that might be a bug with th latest version.  I downloaded an installed a version, and all was good.  Later that night I got a update available notification, so I installed it, and that's when the mouse pointer problem appeared for me....on 3 machines, same scenario.

---

