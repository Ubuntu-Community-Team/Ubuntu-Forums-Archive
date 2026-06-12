---
title: "Trouble with VNC remote desktop"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-05-09
EDIT:  Sorry for posting before googling this issue.  I found the bug report here:  [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126)

I recently did an upgrade to 9.04 on my home PC and up until before that I was VNCing into my PC remotely on a daily basis with no issues.  Since upgrading, here's what happens when I connect:

I see my desktop and everything load up on the remote end of things, but it's just one screen capture.  Clicking on something like the Applications menu for example produces no refresh on the remote end; you seen no change on the screen remotely.  I have a System Monitor widget on my upper panel that I use to watch CPU/RAM/Network activity but that never refreshes either.  So I connect, see whatever happens to be on the screen at that moment, and then it doesn't refresh again, unless I disconnect completely and then reconnect.  Telling my client software to request a refresh does nothing.  However, if I say, click on the applications menu, disconnect, and reconnect, it appears that it actually did pass my click through and displays the menu upon reconnect, only to once again, leave me in standstill before disconnecting and reconnecting again.

---

### Post by crouton on 2009-05-10
Per [http://ubuntuforums.org/showthread.php?t=1154353&highlight=remote+desktop](http://ubuntuforums.org/showthread.php?t=1154353&highlight=remote+desktop) Compiz is preventing screen updates.  Disable it and remote desktop will work.  (Just in case somebody skipped reading the bug report.)

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

