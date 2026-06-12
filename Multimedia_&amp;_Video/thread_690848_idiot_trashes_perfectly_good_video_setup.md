---
title: "idiot trashes perfectly good video setup"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by akahige on 2008-02-07
Been working out the kinks on a dual monitor upgrade. Everything was working a-okay until I tried to build an icon to replace having to dump this into a xterm: "rdesktop -g 1680x1050 -D -P -x l 192.168.2.14:3389". In trying to test the thing, the icon got hit twice and things started breaking.

Now, the -P option -- which allows bitmap caching -- breaks the entire rdesktop display. Instead of the remote screen coming up, a black square of the specified size appears. Carrying this slightly further, I don't think that rdesktop is actually running without video display, because I can't cancel out of the remote login by hitting ESC, which I should be able to do.

There seem to be some other cascading issues, too. Some things -- like xterm -- wants to launch apps onto a different monitor than the one that the term itself is on, but the biggest problem is VMware. Before, it was running perfectly. Now, when I go to run it full screen, it leaves the XFCE bar at the top of the main screen, takes away the application title bar, but otherwise does nothing to resize the virtual desktop. And it can't even find the other monitor. I assume that these issues are related because none of them were previously present, but I can't say for certain.

I looked at my Nvidia setup (using the proprietary driver which works perfectly), and it doesn't look like anything changed. And I assume that if my X config got whacked, then X wouldn't work. Thinking that the -P thing might be related to a cache that needed clearing (but not knowing where to look for such a creature), I rebooted, but that didn't actually help things.

Because I really can't leave well enough alone, before rebooting, I checked for updates. Even though it said it didn't find anything, it did download 13 files which it apparently did nothing with.

So that's my problem. Anybody got any ideas?

---

